### What your current criterion is actually doing

Choosing the threshold where **TPR = TNR** is equivalent to choosing the point where **FPR = FNR** (because TNR = 1 − FPR and FNR = 1 − TPR). This is essentially the **equal error rate (EER)** operating point, and the number you maximize is **1 − EER**.

This can be a reasonable choice only if:

- false positives and false negatives have similar cost, and
    
- you really want a single operating point rather than performance across thresholds.
    

But it has a few important limitations that are easy to improve.

---

## 1) First, make sure ranger is doing classification (this is a common silent issue)

In `ranger`, the “objective” is determined by the **type of the outcome**:

- If your outcome is a **factor**, ranger does **classification**.
    
- If your outcome is **numeric 0/1**, ranger does **regression**, even if it looks like probabilities.
    

If you train ranger on numeric 0/1, you get regression splits (variance reduction), not classification splits (Gini/entropy), and the output is not a proper class-probability model in the classification sense. It may still be between 0 and 1, but it is not the same learning problem.

**Improvement**

- Ensure `y` is a factor for ranger classification.
    
- Use probability predictions explicitly.
    

Typical pattern:

- train with `y` as factor and `probability = TRUE`
    
- predict with probabilities (depending on your call, often `type = "response"` returns a probability matrix when `probability=TRUE`, otherwise use `type="prob"`)
    

This alone can materially change results.

---

## 2) Separate three decisions that are currently mixed together

Right now, you are implicitly doing all three at once:

1. learn a scoring function
    
2. pick a threshold
    
3. report a single thresholded metric
    

Better practice is:

- Train models to produce a **good ranking and/or good probabilities**.
    
- Choose the threshold **based on the real decision objective**.
    
- Evaluate with metrics that reflect both, not just one operating point.
    

Why: two models can have similar “TPR at EER” but behave very differently at other thresholds, and one can be much better calibrated.

---

## 3) Add threshold-free metrics (you will learn more and choose better)

Your current metric uses exactly one threshold. Add at least one threshold-free metric to compare models more robustly:

- **ROC AUC**: good for ranking quality across thresholds.
    
- **PR AUC**: often more informative if the positive class is rare.
    
- **Log loss (cross-entropy)**: evaluates probability quality and strongly penalizes confident wrong predictions.
    
- **Brier score**: probability accuracy with a more interpretable scale than log loss.
    

What to expect:

- It is common that model A wins on ROC AUC while model B wins on log loss (calibration differences).
    
- XGBoost often looks strong on AUC, but its raw probabilities can be miscalibrated unless you tune and/or calibrate.
    

---

## 4) Your “TPR = TNR” threshold can be a poor choice under class imbalance

Even if you truly value sensitivity and specificity equally, the practical consequences depend heavily on prevalence.

Example (to show the failure mode):

- prevalence = 1%
    
- you pick a threshold giving TPR = TNR = 0.90  
    then FPR = 0.10
    
- precision becomes:  
    PPV = (0.01×0.90) / (0.01×0.90 + 0.99×0.10) ≈ 0.083
    

So you would have **90% sensitivity and 90% specificity**, yet only **about 8% of predicted positives are truly positive**. If positives trigger costly actions, this is unacceptable.

**Improvements (choose one depending on real needs):**

- If you want “treat classes equally” in evaluation: **maximize balanced accuracy** = (TPR + TNR)/2, rather than forcing TPR = TNR. Forcing equality is not necessary and can reduce achievable performance.
    
- If you want “errors equally likely”: your approach is fine conceptually, but:
    
    - pick the threshold on validation data only
        
    - report confidence intervals because it can be noisy
        
- If you have asymmetric costs: choose threshold by **expected cost / expected utility**, not by equalizing rates.
    

---

## 5) Do threshold selection inside resampling (avoid optimistic bias)

A very common leakage pattern is:

- tune model and threshold using the same data used to report performance
    

Even if you have a train/test split, if you choose the threshold using the test set (directly or indirectly), results are optimistic.

**Improvement**  
Use one of these:

- **Nested cross-validation** (best general approach):
    
    - inner loop: tune hyperparameters, optionally calibrate, choose threshold
        
    - outer loop: estimate performance on held-out folds
        
- Or a simpler approach:
    
    - train set for fitting/tuning
        
    - validation set for threshold selection
        
    - final untouched test set for one-time reporting
        

What to expect:

- Your reported “equal TPR/TNR value” will usually drop, sometimes noticeably, because threshold selection overfits too.
    

---

## 6) Tune both models properly (defaults are rarely comparable)

### XGBoost

You are using `binary:logistic`, which is appropriate, but performance depends heavily on tuning and regularization:

Key parameters to tune:

- `nrounds` with **early stopping**
    
- `eta` (learning rate)
    
- `max_depth`
    
- `min_child_weight`
    
- `subsample`, `colsample_bytree`
    
- `gamma`
    
- `lambda` (L2), `alpha` (L1)
    

If imbalance exists:

- `scale_pos_weight` often helps ranking and training stability.
    

Also explicitly set an evaluation metric during tuning (example: `"logloss"`, `"auc"`, `"aucpr"`), depending on what you care about.

### ranger

Tune at least:

- `mtry`
    
- `min.node.size`
    
- `sample.fraction`
    
- `num.trees` (often enough once stable, but ensure convergence)
    
- consider class weights or sampling if imbalance is strong
    

What to expect:

- With reasonable tuning, XGBoost frequently wins on ROC AUC for tabular problems with interactions and nonlinearity.
    
- Random forests can be more robust with less tuning and sometimes win when signal-to-noise is low or data is smaller.
    
- Differences may be small; uncertainty intervals matter.
    

---

## 7) Calibrate probabilities (especially if you will threshold)

Tree ensembles often produce **poorly calibrated probabilities** out of the box:

- Random forests often produce probabilities that are too “compressed” toward the center.
    
- Boosting can produce probabilities that are too extreme.
    

If your downstream decision depends on a threshold, calibration can improve stability and decision quality.

**Improvement**  
After fitting, calibrate on validation folds only:

- Platt scaling (logistic calibration)
    
- isotonic regression
    
- or beta calibration
    

What to expect:

- Calibration often improves **log loss / Brier** and makes threshold choices more transferable.
    
- Calibration usually does **not** change ROC AUC much (AUC is ranking-based), but it can change thresholded metrics substantially.
    

---

## 8) Report more than one operating point

If you deploy a model, one threshold is rarely enough to understand behavior.

At minimum, for the chosen model:

- confusion matrix at chosen threshold
    
- TPR, TNR, PPV (precision), NPV
    
- plus ROC AUC and PR AUC
    
- plus calibration (Brier/logloss or a calibration plot)
    

What to expect:

- You may find that two models with similar “TPR=TNR value” have very different precision, which changes real usefulness.
    

---

## 9) Check data structure assumptions (this can dominate everything)

With 350 predictors, performance validity depends strongly on how you split:

- If you have repeated measurements per person, site, device, time period: use **grouped splits**.
    
- If it is time-ordered prediction: use **time-based validation**, not random CV.
    
- Ensure preprocessing (imputation, encoding) happens **within folds**.
    

What to expect:

- Correct splitting often reduces headline metrics, but gives you deployable truth.
    

---

# Summary of concrete upgrades

If you do only a few things, do these:

1. **Ensure ranger is classification** (outcome as factor; probability predictions correctly).
    
2. Use **nested CV** (or train/validation/test) so hyperparameters and threshold are chosen without leaking into evaluation.
    
3. Compare models with at least **ROC AUC + PR AUC + log loss (or Brier)**, not only “TPR at TPR=TNR threshold”.
    
4. Choose threshold based on **utility/cost**, or at least maximize **balanced accuracy** instead of forcing equality.
    
5. **Calibrate probabilities** if thresholding matters.
    

---

# What results you should expect after improving the setup

- Your reported performance at the chosen threshold will usually become **lower but more reliable** once threshold selection is done correctly (nested CV or proper validation).
    
- You may find that the “best” model by your current EER-based metric is not best by PR AUC or by expected utility, especially under class imbalance.
    
- If ranger was inadvertently run as regression (numeric 0/1 outcome), switching to proper classification can change results substantially and often improves classification behavior.
    
- Calibration may not improve AUC, but it can noticeably improve real decision quality at a fixed threshold and reduce threshold instability across folds or time.
    

If you want, I can translate this into a specific resampling and tuning plan in R (for example with tidymodels or mlr3), including how to tune the threshold inside folds and how to compute EER, balanced accuracy, PR AUC, and calibration metrics without leakage



---
---
---


A repeated value around 0.67 to 0.68 across “different dependent variables” is usually a red flag, not something I would treat as a meaningful coincidence. Whether it is a problem in setup or a real phenomenon depends on what exactly is returning 0.67 to 0.68.

There are three common interpretations, each with different causes.

## 1) If the per-row predicted probabilities are almost constant at 0.67 to 0.68

That typically means the model is behaving close to an intercept-only model, it is predicting something like the base rate for everyone, with very little discrimination.

### Why this happens

**A. The model is not learning splits at all (or almost none)**

- XGBoost can end up close to constant if it effectively cannot find gainful splits (features have no signal, or hyperparameters are too restrictive).
    
    - Examples: very strong regularization, too few boosting rounds, early stopping stopping almost immediately, min child weight too large, gamma too large.
        
- Ranger can do something similar if trees hardly split (for example, `min.node.size` too large, or predictors have low usable variation).
    

**B. Your feature matrix is effectively unusable**  
Common ways this happens in R:

- You accidentally feed XGBoost a matrix that is mostly constant or mostly missing.
    
- A preprocessing step (encoding, filtering, scaling) drops most information.
    
- Many predictors are factors with unseen levels in prediction data, and you end up with lots of NAs or all-zero dummy variables.
    

**C. You are accidentally applying a sigmoid twice**  
This is more common than it sounds.

- With `objective = "binary:logistic"`, `predict(xgb_model, ...)` already returns probabilities in (0, 1).
    
- If you then do `plogis(pred)` again, you compress the entire range:
    
    - `plogis(0) = 0.50`
        
    - `plogis(0.7) ≈ 0.67`
        
    - `plogis(1) ≈ 0.73`
        

So even if the true probabilities vary widely, after an extra `plogis` they all get squeezed into roughly 0.50 to 0.73, and with rounding you can easily see mostly 0.67 to 0.68.

**D. Ranger is accidentally running regression, not classification**  
If your outcome is numeric 0/1, `ranger()` defaults to regression unless the outcome is a factor. Then the predicted value can behave like a smoothed mean response, often close to the prevalence, and may not vary much.

### How to diagnose quickly

Do these checks for each trained model:

1. Check spread of predictions (on a holdout set, not training):
    

- `sd(pred)`
    
- `quantile(pred, c(.01, .05, .5, .95, .99))`
    

If `sd(pred)` is tiny and the quantiles are nearly identical, your model is essentially constant.

2. Compare mean prediction to prevalence:
    

- `mean(y_valid)` versus `mean(pred_valid)`
    

If `mean(pred_valid)` is extremely close to `mean(y_train)` (or `mean(y_valid)`) and there is almost no spread, you are near an intercept-only solution.

3. For XGBoost, check whether training actually improved:
    

- Look at training logloss (or AUC) over iterations.
    
- Check feature importance. If all gains are near zero or importance is empty, it did not learn meaningful splits.
    

What this implies: if predictions are almost constant, the reason is almost always setup/preprocessing/parameter constraints, not “the task is equally predictable.”

---

## 2) If the “0.67 to 0.68” is the threshold you choose (where TPR = TNR)

This can also cluster tightly across outcomes, even when true predictability differs, for reasons that have nothing to do with “model strength.”

### Why this happens

**A. Your predicted probabilities are miscalibrated in a similar way across tasks**  
Tree ensembles often have systematic calibration bias. If all your models produce similarly shaped score distributions, the equal-error-rate threshold can land in a similar region again and again.

**B. Similar class prevalence across dependent variables**  
If many of your outcomes have prevalence near 0.67, and your model is only weakly discriminative, the threshold that balances TPR and TNR often ends up near the region where scores pile up, which frequently tracks the base rate.

**C. You choose the threshold on the same data you evaluate on**  
This makes the threshold look stable and “good,” and it can also make different targets look more similar than they really are.

### Diagnostic

Compute the threshold separately inside each cross-validation fold and look at its variability. If the fold-specific thresholds bounce around, your single value 0.67 to 0.68 is not a stable property of the problem, it is an artifact of a particular split.

---

## 3) If “0.67 to 0.68” is your reported performance (the equal TPR/TNR value)

This can be real, but it is also commonly an artifact.

### Why this happens

**A. Discreteness and rounding of TPR/TNR**  
TPR and TNR are ratios of integers. If you have, say, 50 positives, TPR can only take values 0/50, 1/50, 2/50, … which are steps of 0.02. With the constraint “TPR approximately equals TNR,” you can easily land repeatedly on the same achievable step like 0.68 (34/50) or 0.67 (depending on sample counts). With small to moderate validation sizes, repeated 0.67 to 0.68 is not surprising even if underlying performance differs.

**B. Your metric is not very sensitive**  
Forcing the operating point to satisfy TPR = TNR throws away information about the rest of the ROC curve. Two outcomes can have meaningfully different AUC or PR AUC, yet have similar equal-error-rate performance.

**C. Sampling noise overwhelms true differences**  
If your test set is not large (especially not large in both classes), the uncertainty on a rate like 0.67 can easily be several percentage points. Outcomes with “true” performance 0.64 vs 0.71 might both be observed around 0.67 to 0.68 depending on the split.

**D. Coding bug or reuse of predictions**  
If you accidentally reuse the same prediction vector when switching dependent variables, you can easily get the same performance repeatedly. This is more common than expected when looping over targets.

### Diagnostics

- For each target, also compute ROC AUC, PR AUC, and log loss. If those vary but your equal-rate metric does not, your metric is masking differences.
    
- Compute uncertainty:
    
    - repeated CV, or bootstrap the test set and recompute the metric
        
    - if the bootstrap interval width is, for example, ±0.03, then 0.67 vs 0.68 is effectively identical
        
- Check whether predictions differ across targets:
    
    - correlation between prediction vectors for different targets should not be 1.0 unless the targets are extremely aligned or something is wrong.
        

---

## What is most likely here?

- If you literally only see two predicted values across all rows (0.67 and 0.68), the most likely causes are:
    
    1. an accidental transformation such as `plogis()` applied to probabilities,
        
    2. a near-constant model because it is not learning,
        
    3. you are extracting the wrong object from the prediction output.
        
- If the “0.67 to 0.68” is your single-number evaluation (equal TPR/TNR), the most likely causes are:
    
    1. discreteness plus rounding and limited test-set size,
        
    2. metric insensitivity to differences between tasks,
        
    3. threshold selection and evaluation not properly separated.
        

---

## Minimal checks that usually locate the issue in minutes

For each dependent variable, on a proper holdout set:

1. `mean(y)`, `mean(pred)`, `sd(pred)`, prediction quantiles.
    
2. AUC, PR AUC, log loss.
    
3. Confirm ranger is classification (outcome is factor) and XGBoost labels are truly 0/1 numeric.
    
4. Confirm you did not apply `plogis()` or another link function to already-probabilistic outputs.
    

If you share which of the three “0.67/0.68” quantities it is (raw probabilities, chosen threshold, or equal-rate metric), the explanation becomes much sharper, but the above covers the main mechanisms that produce exactly what you are seeing.