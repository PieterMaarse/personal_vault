---
MOC:
tags:
  - note
date: 2026-02-20
about:
gearchiveerd:
inhoudelijk:
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
### ~~Before you rewrite anything: make 2 top-level decisions~~

1. ~~**Decide the primary contribution**~~
    

- ~~**Track A (policy targeting study):** you claim something about whether RVU users are in “demanding work” (as proxied). Then you must fix timing, leakage, misclassification theory, and add uncertainty.~~
    
- ~~**Track B (methods/cautionary thesis):** you show that with predicted survey proxies and weak transportability, the policy question is not identified and results are highly assumption-sensitive. Then you should _stop presenting point conclusions as “main results”_ and make the robustness/bounds the centerpiece.~~
    

2. ~~**Resolve the “irrecoverable mistakes” problem**~~
    

- ~~If the reported samples/weights have known errors, you should not keep the current numerical results as if they are credible. Either:~~
    
    - ~~re-run and correct the analysis, or~~
        
    - ~~remove the affected tables/claims and explicitly reframe as partial/illustrative with a verified subset (for example only LISS test-set validation, overlap sample diagnostics, and bounds).~~
        

~~Everything else depends on these two choices.~~

---

## Front matter

### ~~Title page~~

~~**Rewrite/add**~~

- ~~Consider whether “AI-generated survey responses” overclaims. You are doing supervised ML prediction from administrative covariates, not generative AI. A safer title is along the lines of “Predicting survey proxies of demanding work using administrative microdata to study RVU users”.~~
    

~~**Fix**~~

- ~~Ensure consistent capitalization and remove any unnecessary disclaimers beyond the VU required one.~~
    

### Abstract

**Rewrite goal:** make the estimand, time alignment, and identification limits unambiguous.  
**Add**

- A one-sentence definition of what you actually estimate (example: “the share of RVU users predicted to have each demanding-work proxy, and their overrepresentation relative to controls”).
    
- A one-sentence statement that conclusions rely on transportability of misclassification rates and are therefore sensitivity/bounds-based, not definitive.
    

**Rewrite/remove**

- Replace “evaluate efficiency” language unless you actually define efficiency as a targeting metric.
    
- Avoid “suggests” without specifying whether that comes from point estimates or from robustness regions.
    

### ~~Acknowledgements~~

~~**Fix**~~

- ~~Spacing typo (“thesis.In particular,”).~~
    
- ~~Keep as is otherwise.~~
    

### Table of contents

**Add**

- If you implement Track A: add a subsection titled **“Identification and estimands”** (either in Section 1 or as 3.0).
    
- If you implement Track B: add a subsection titled **“Partial identification / bounds”** and make robustness central.
    

---

## 1 Introduction

### 1.1 Motivation and research question

**Rewrite goal:** align the research question with what the design can answer.  
**Add**

- A paragraph defining:
    
    - what “demanding work” means _in this thesis_ (explicitly: which proxy dimensions you can observe),
        
    - what “works” means (targeting vs coverage vs welfare).
        
- A crisp statement of the estimand(s):
    
    - $\alpha_1 = P(X=1 \mid Y=1)$ (composition among RVU users)
        
    - $\Psi$ (overrepresentation vs controls)
        

**Rewrite/remove**

- Replace “efficiency” throughout unless you define it as “targeting precision” (share of users in intended group).
    
- Remove the placeholder “(toevoegen)” and replace with a sourced claim or drop the sentence entirely.
    
- Tighten the literature gap: clearly separate “what is known about who uses RVU” vs “what is known about demandingness”.
    

**Add (optional but high value)**

- A short “contributions” list:
    
    1. method: predicting survey proxies from admin data,
        
    2. empirical: descriptive targeting patterns (conditional on assumptions),
        
    3. methodological: sensitivity to differential misclassification.
        

### 1.2 Procedure and problems

**Rewrite goal:** turn this into a research design + identification overview.  
**Add**

- A simple pipeline figure or numbered workflow:
    
    1. choose proxies X from LISS,
        
    2. train prediction model on respondents (with clear unit: person-year vs person),
        
    3. predict for RVU users and controls in the relevant pre-RVU year,
        
    4. correct using Se/Sp,
        
    5. perform sensitivity analysis.
        

**Critical rewrite**

- Fix the **time logic**. “Predictions are made for 2020” is only coherent if your RVU users are 2021 starters only. If you include 2021–2025 users, you need individual-specific “last working year before RVU start” or restrict the RVU sample.
    
- Explicitly state what cannot be learned due to case-control sampling: you cannot estimate take-up $P(Y=1\mid X=1)$.
    

**Add**

- A short “key assumptions” box:
    
    - transportability of Se/Sp from respondents to controls,
        
    - (stronger) transportability to RVU users or use of bounds if not.
        

### 1.3 Structure

**Rewrite**

- Update after adding/removing sections above.
    

---

## 2 Background

### 2.1 The RVU levy exemption

**Rewrite goal:** make the policy institutional details support your empirical design.  
**Add**

- Clarify exactly how “RVU user” is observed in your data and what the UWV-provided info contains (start date? amount? duration? only code 53?).
    
- A short paragraph on the distinction between “using an RVU arrangement” and “using the levy exemption” and why your operational definition matches the latter (or acknowledge mismatch).
    

**Rewrite**

- If you use “efficiency”, define it here in policy terms and then explicitly say you use targeting proxies instead.
    

### 2.2 Gezond naar het Pensioen

**Add**

- A short mapping between what TNO assesses (load fields) and what your proxies cover, explicitly noting gaps.
    

### 2.3 Demanding jobs

**Rewrite goal:** justify proxies and limitations systematically.  
**Add**

- A table: TNO load fields vs your LISS items (covered / partially covered / not covered).
    
- One paragraph: why self-reported LISS measures are still meaningful, but imperfect (and how that affects interpretation).
    

---

## 3 Theoretical framework

### 3.0 New subsection: Estimands and identification (strongly recommended)

**Add**

- Define “targeting metrics” you estimate and what would be needed for causal “policy effectiveness”.
    
- State clearly: your study is not causal in the sense of estimating the effect of RVU on outcomes.
    

### 3.1 Entities of interest

~~**Fix**~~

- ~~The reference “Table 1e” for α\alphaα is incorrect (it’s $P(X\mid Y)$, not $P(\hat X\mid Y)$. Correct the table reference.~~
    

**Rewrite**

- Clarify the two comparisons:
    
    - RVU vs employed non-users,
        
    - RVU vs age-matched eligible non-users,  
        and justify both.
        

### 3.2 The misclassification problem

~~**Critical fix**~~

- ~~Correct the nondifferentiality statement. You currently write P(X∣X^,Y)=P(X∣X^)P(X\mid \hat X, Y)=P(X\mid \hat X)P(X∣X^,Y)=P(X∣X^). For nondifferential misclassification you need P(X^∣X,Y)=P(X^∣X)P(\hat X\mid X, Y)=P(\hat X\mid X)P(X^∣X,Y)=P(X^∣X). Rewrite the definition and adjust subsequent text accordingly.~~
    

**Add**

- A short paragraph explaining why nondifferentiality is plausible for controls (maybe) but not for RVU users, linking forward to your diagnostics.
    

### 3.3 Misclassification due to prediction errors

**Rewrite goal:** connect the ML setup to the misclassification correction cleanly.  
**Add**

- A paragraph distinguishing:
    
    - “prediction error” due to imperfect $P(X\mid Z)$,
        
    - “transport error” due to covariate shift or concept shift between respondents and RVU users.
        

**Rewrite**

- If you keep the density-region explanation, tighten notation and reduce repetition. This section currently risks looking mathematically heavy without improving identification.
    

### 3.4 Nondifferentiality of prediction errors

~~**Fix**~~

- ~~Remove the corrupted sentence fragment in the section intro (“practice.ments…”).~~
    
- ~~Fix Figure 4 caption (“When true X is unknown,.”).~~
    

**Add**

- A concrete diagnostic plan:
    
    - compare covariate distributions (standardized mean differences) respondents vs employed/eligible,
        
    - compare model calibration or error rates across observable strata (age, sector, education),
        
    - exploit the LISS–RVU overlap as an internal validation subset (even if selected).
        

**Add (if Track B)**

- Formalize your robustness as partial identification:
    
    - define the plausible set for Se,Sp,
        
    - show how conclusions depend on regions, not points.
        

---

## 4 Data

### 4.1 CBS Microdata

**Add**

- A reproducible “data dictionary” table: each dataset, unit (person-month), key variables used, years used, and what gets aggregated.
    

### 4.2 RVU users

**Rewrite goal:** make sample definition defensible and transparent.  
**Add**

- Exact inclusion criteria:
    
    - which years of RVU users (2021–2024? 2021–2025?),
        
    - how you treat multiple spells,
        
    - whether you observe RVU start year and how.
        
- A flow diagram: starting N, after linkage, after requiring SPOLIS presence in target year, etc.
    

**Fix**

- If many RVU users do not appear in SPOLIS 2020, you must address what “pre-RVU employment” means and whether the sample is biased.
    

### 4.3 LISS Work and Schooling survey

**Rewrite goal:** improve construct validity of proxies.  
**Critical rewrite**

- Reconsider coding “supervisory” as “demanding”. If you keep it, it must be justified as a demanding-work proxy (currently it is not). Prefer: drop it, or treat as a separate descriptive covariate, not a demandingness indicator.
    

**Add**

- For each selected LISS question:
    
    - exact wording (by wave if changed),
        
    - response scale,
        
    - your binarization rule,
        
    - a brief justification and at least one robustness alternative threshold.
        

**Add**

- Address repeated measures:
    
    - explain whether you train on person-wave rows and how you prevent individuals with many waves dominating.
        

### 4.4 Comparison groups

**Rewrite goal:** make the sampling logic consistent with your identification story.  
**Add**

- Exact sampling procedure in step order (so selection bias is traceable).
    
- A table of sample sizes after every filtering step for each group.
    

**Rewrite**

- The argument “LISS is representative therefore respondents should match employed controls” is contradicted by your own Figure 5. Rewrite this as an empirical question and present formal balance metrics (not only bar charts).
    

**Add**

- If Track A: propose a weighting scheme so the training sample matches the target population (domain adaptation / importance weighting) or explicitly state you cannot and move to Track B framing.
    

---

## 5 Predictions

### 5.1 Machine Learning models

**Add**

- A short justification of why RF/XGBoost are appropriate given the feature types and sample size.
    
- A note on interpretability: you claim black box is fine, but you still need to check for leakage and stability.
    

### 5.2 Features

**Critical rewrite**

- Remove any use of information “after” the target year if that can be post-RVU or post-retirement related. Your current feature windows include “1 year after”, which risks post-treatment leakage.
    

**Add**

- A table listing feature blocks by time window, explicitly marking which are used in final models.
    

### 5.3 Training and tuning

~~**Fix**~~

- ~~You wrote you weight observations so each group (Y=1 and Y=0) has equal total weight. That is wrong: you predict X, so the class weights should balance X=1X=1X=1 vs X=0X=0X=0. Correct the text and verify the implementation.~~
    

**Add**

- Clear evaluation metrics:
    
    - Se, Sp, Youden’s J (already),
        
    - plus precision/PPV and calibration checks (because your conclusions depend on prevalence).
        

**Add**

- Clarify unit of split: person-level split is good, but then address multiple waves per person.
    

### 5.4 Estimating sensitivity and specificity

**Add**

- Uncertainty: confidence intervals via bootstrap on the test set for Se/Sp.
    
- Stratified performance beyond age: sector, education, gender, income bands.
    

**Rewrite**

- Explain why age-weighted Se/Sp is intended to approximate eligible controls, but why it still may not approximate RVU users.
    

---

## 6 Evaluation

### 6.1 Does the RVU levy exemption work?

~~**Rewrite goal:** present results as targeting patterns under explicit assumptions, with uncertainty.~~  
~~**Fix**~~

- ~~“full unemployed population” should be “employed population”.~~
    

**Rewrite**

- Table 5 needs to be restructured:
    
    - clearly separate comparisons vs employed and vs eligible,
        
    - show $\hat\alpha_1$​, $\hat\alpha_0​$ for each control, then $\hat\Psi$,
        
    - add confidence intervals (or at least bootstrap bands).
        

**Add**

- A short interpretation guardrail after Table 5:
    
    - what conclusions are stable across plausible Se/Sp,
        
    - what conclusions are not.
        

### 6.2 Robustness

**Rewrite goal:** make this the centerpiece if identification is weak.  
**Add**

- Define the “plausible” region for Se/Sp more explicitly:
    
    - informed by test-set estimates,
        
    - and by overlap-sample estimates if you can compute them.
        
- Summarize Figure 8 in a table: for each proxy, whether overrepresentation holds for (a) most plausible region, (b) only small region, (c) ambiguous.
    

**Add (high impact)**

- If you have any LISS–RVU overlap with observed proxies X, use it here:
    
    - show Se/Sp on overlap vs on general test set,
        
    - show how conclusions shift.
        

---

## 7 Conclusion and discussion

### 7.0 Conclusion

**Rewrite goal:** separate “what you measured” from “what you wish you could measure.”  
**Rewrite**

- Replace “efficiency” with “targeting” unless redefined earlier.
    
- Tone down claims: move from “we conclude it reached its intended target” to “under assumptions A and within plausible error regions, indicators B and C suggest overrepresentation; for others the evidence is weak”.
    

### 7.1 Discussion

**Critical rewrite**

- The paragraph stating you made mistakes you cannot recover is not acceptable in its current form if results remain in the thesis.
    
    - Either remove incorrect results and keep a verified subset, or re-run and correct.
        
- Rewrite limitations in standard categories:
    
    - measurement of X (self-report),
        
    - prediction error and transportability,
        
    - sampling/representativeness and covariate shift,
        
    - timing alignment and potential leakage,
        
    - uncertainty quantification.
        

### 7.2 Further research

**Rewrite**

- Make it concrete and prioritized:
    
    1. obtain an internal validation sample (overlap or another survey),
        
    2. correct timing to “last working year”,
        
    3. add health/job exposure data if possible,
        
    4. evaluate post-2026 targeted regime once available.
        

---

## Appendix and references

### Appendix A

**Add**

- A reproducibility appendix: pseudo-code for sampling steps and feature construction.
    
- Additional balance tables and calibration plots (if allowed under disclosure rules).
    

### Bibliography

**Fix**

- Spelling error “werzaamheden” → “werkzaamheden”.
    
- Ensure all policy documents are cited consistently and that access dates are consistent.
    

---

## Minimal set of rewrites that will most improve examiner confidence

If you want a shortest-path plan, do these first:

1. Fix estimand language: stop calling it “efficiency” unless defined as targeting.
    
2. Fix timing: ensure the predicted year matches “pre-RVU” for your RVU sample, or restrict the RVU sample.
    
3. Remove leakage: no post-target-year predictors.
    
4. Correct misclassification theory statement and notation.
    
5. Add uncertainty (bootstrap CIs) and elevate robustness/bounds to the main result.
    
6. Remove or reclassify “supervisory” as a demanding-work proxy, or justify it convincingly.
    

If you apply these changes, the thesis becomes substantially more defensible even if the final substantive conclusion remains cautious.