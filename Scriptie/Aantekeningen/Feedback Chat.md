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

## Overall assessment

The thesis tackles an important, policy-relevant question and is transparent about limitations. The central idea, using administrative microdata to predict survey-based “demanding work” proxies and then correcting for misclassification, is interesting and potentially publishable as a methodological note.

At the moment, however, several issues materially weaken the credibility of the empirical conclusions:

- The core estimand “efficiency” is not defined in a way that matches what you actually estimate.
    
- Identification hinges on assumptions you (correctly) argue are unlikely, but you still present point conclusions without uncertainty quantification.
    
- There are theoretical inconsistencies in the misclassification section.
    
- There are internal red flags about data construction and weighting that you explicitly acknowledge as “mistakes” you could not recover due to lost CBS access, which is not acceptable if the thesis is meant to support substantive findings.
    

If you fix the conceptual definition, clean up the theoretical framework, and either (a) repair the data/sampling/weighting and add uncertainty, or (b) reframe the thesis as primarily a cautionary methodological demonstration showing why the evaluation is not identified with available data, the thesis can become substantially stronger.


## Major issues that require revision

### 1) “Efficiency” is not the right estimand and is not defined

You ask: “How efficient is the RVU levy exemption to support people with demanding jobs with early retirement?” (Section 1.1). But the analysis estimates:

- Shares: $P(X=1\mid Y=1)$ (fraction of RVU users predicted to have demanding work)
    
- Representation comparisons via odds ratios comparing $P(X=1\mid Y=1)$ to $P(X=1\mid Y=0)$ (Section 3.1, 6.1)
    

This is **targeting / composition**, not “efficiency” in the policy evaluation sense (which would involve costs, benefits, welfare, or at least leakage vs coverage). If you keep your current design, rename throughout:

- “Efficiency” → “targeting”, “alignment with intended target group”, or “degree of targeting”
    
- Or define “efficiency” explicitly as a targeting metric (for example: “efficiency is the share of users that are in the intended group, and overrepresentation relative to eligible workers”).
    

Actionable fix:

- Add a short subsection in 1.1 defining the estimand(s) formally in words before equations.
    
- Be explicit that you do **not** estimate take-up among demanding workers $P(Y=1\mid X=1)$ (you note this, but it should be more prominent because it is central to whether the policy “supports” the group).
    
    
    

### 2) The timing logic is likely incorrect: “predict for 2020” does not match “year before retirement” for all users

You state: “Since the exemption came into effect in 2021, all users should have been part of the employed population the year before, and hence, predictions are made for 2020.” (Section 1.2). This is only true for users whose RVU starts in 2021. If your RVU user dataset covers 2021–2025 (which you imply), then many users’ “year before RVU” is 2021–2024, not 2020.

This matters a lot because:

- You may be measuring demandingness at the wrong time for a large fraction of users.
    
- Covariates can change substantially between 2020 and the last working year (sector switches, hours reductions, accommodations, health shocks).
    

Actionable fixes (pick one, depending on feasibility):

1. **Best**: define an individual-specific target year = last observed “regular employment” year before RVU start, and construct the same for controls (matched by age and calendar year).
    
2. If that is infeasible: restrict the analysis sample to RVU users starting in 2021 only, so that “predict in 2020” is coherent.
    
3. If you keep the 2020 approach: you must reframe the question as “What did their predicted demanding-work proxies look like in 2020 (pre-RVU era), compared to others?” which is weaker and not “before they retired.”
    

Right now this is a conceptual mismatch between your motivation and what is actually measured.



### 3) Potential post-treatment leakage: you use features “after” the target year

In Section 5.2 you state you use time windows relative to the target year including “1 year after” etc. If the target year for RVU users is 2020, “after” windows include 2021 and later, when RVU participation may occur.

That is a major problem because you risk using variables affected by RVU use (income changes, employment relationship codes, hours dropping, sector exit) to predict “demanding work,” which:

- inflates apparent predictive performance on respondents (if similar patterns exist),
    
- and, more importantly, makes misclassification **differential by construction** between exempted and non-exempted groups.
    

Actionable fix:

- Restrict predictors to information available **at or before** the target year (and ideally before the “decision” year).
    
- Include a clear table listing predictor blocks by time window and state explicitly which are used in the final models and why.
    
    
    

### 4) Theoretical inconsistency: nondifferential misclassification is misstated

In Section 3.2 you write nondifferentiality as:

$$P(X \mid \hat{X}, Y) = P(X \mid \hat{X})$$

and claim it is equivalent to $\theta_{\hat{x}\mid x,y}=\theta_{\hat{x}\mid x}​$ (Eq. 5). These are **not equivalent** in general.

For nondifferential misclassification you want:

$$P(\hat{X}\mid X, Y)=P(\hat{X}\mid X)$$

That is exactly $$\theta_{\hat{x}\mid x,y}=\theta_{\hat{x}\mid x}$$​. The expression $P(X\mid \hat{X},Y)$ is a reclassification probability and will typically depend on Y even when misclassification is nondifferential, because $P(X\mid Y)$ differs across groups.

Actionable fix:

- Replace Eq. (5) with the correct nondifferential condition $P(\hat{X}\mid X,Y)=P(\hat{X}\mid X)$.
    
- Keep your footnote about reclassification probabilities, but make the distinction explicit and consistent throughout.
    
    
    

### 5) The “severe limitations” you admit undermine the credibility of the reported results

In the Discussion you state you made “several mistakes” in constructing comparison samples and that the weighting procedure “does not work as intended” (Section 7.1). This is a critical problem: it implies that key reported numbers may be wrong, and you cannot defend them.

In a thesis, this needs to be resolved one way or another:

- Either re-run and correct the analysis (strongly preferred),
    
- or remove/replace the affected results and present only what you can verify,
    
- or reframe the thesis as a methodological exploration with simulated data and a limited verified empirical illustration.
    

Leaving incorrect computations in place but discussing them as irrecoverable will likely be viewed as fatal by examiners.

### 6) You may already have a partial validation dataset: exploit the LISS–RVU overlap

In Section 4.4 you note a “small sample” of individuals who are both LISS respondents and RVU users, but you assign them to the respondents group (1). That is a missed opportunity.

Those overlap individuals are potentially extremely valuable because they provide:

- Y=1 and observed (self-reported) proxies X for at least some RVU users,
    
- allowing you to directly test whether misclassification differs by Y (at least for the subset who appear in LISS and match to CBS).
    

Yes, overlap may not be random (you even mention supervisory overrepresentation), but you can still:

- compare error rates for overlap RVU users vs non-RVU respondents within the same covariate strata,
    
- or use matching/weighting to approximate the RVU distribution (age, sector, income) and show sensitivity.
    

Actionable fix:

- Add a subsection: “Internal validation using LISS–RVU overlap” and quantify sample size.
    
- Report sensitivity/specificity for the overlap group and compare to the main test set.  
    This could materially strengthen your argument about nondifferentiality being implausible, and may partially rescue identification.
    
    
    

### 7) No uncertainty quantification for corrected estimates and odds ratios

You report corrected point estimates for $\hat{\alpha}$ and $\hat{\Psi}$ (Table 5) but provide no confidence intervals, and the correction formula can amplify variance substantially when $Se+Sp$ is close to 1.

Actionable fix options:

- Bootstrap at the individual level (resample respondents, retrain or at least re-estimate Se,Sp, and propagate through corrections).
    
- If retraining is too expensive, use a two-stage approach: treat model predictions fixed, bootstrap Se,Sp and the contingency counts, then delta method for corrected $\alpha$ and $\Psi$.
    
- At minimum, provide sensitivity bands or plausibility intervals beyond Figure 8.
    

Right now, the reader cannot distinguish “statistical noise” from “substantive differences.”



## Medium-priority design and interpretation issues

### 8) The demanding-work proxies need tighter conceptual alignment with the policy definition

Section 2.3 lists TNO load fields. Your selected LISS questions cover a narrow part of physical load and working times, and nothing directly on psychosocial, cognitive, environmental loads (except indirectly). That is not necessarily wrong, but then your conclusions must be restricted accordingly.

Actionable improvements:

- Add a table mapping each chosen LISS item to TNO load fields (and explicitly list missing fields).
    
- Be explicit that you are evaluating targeting to _selected observable aspects_ of demanding work, not “demanding work” in general.
    
    
    

### 9) Question (a) “profession supervisory” is not a demanding-work proxy as currently used

You convert a 9-category profession item to mental/manual/supervisory and then code supervisory as “demanding” (Section 4.3). This is conceptually hard to defend. Supervisory roles are not inherently “demanding” in the same way, and may be inversely related to physical demands.

You justify inclusion because RVU users are overrepresented in the overlap group, but that is not a valid conceptual reason to label it as demanding work.

Actionable fixes:

- Remove question (a) from the demanding-work set, or treat it as a separate descriptive exercise (“who is overrepresented among RVU users”).
    
- If you keep it, you must justify why “supervisory” corresponds to the policy’s target group (which is unlikely), or redefine the binary classification (for example manual vs non-manual might be more defensible, but still imperfect).
    
    
    

### 10) Binary thresholding of ordinal items discards information and creates arbitrary classification

You dichotomize “never/sometimes/often” as demanding only if “often,” and “agree/strongly agree” similarly (Section 4.3). That is a strong modeling choice that should be justified and tested.

Actionable fixes:

- Add robustness checks with alternative thresholds (sometimes-or-often vs never, etc.).
    
- Consider modeling the ordinal outcome directly (ordinal classification) or using predicted probabilities of each category and defining demandingness probabilistically.
    
- At minimum, show how prevalence of “often” differs by age/sector to motivate why “often” is the right cutoff.
    
    
    

### 11) Repeated measures and weighting in the training set

You have up to 17 waves per respondent (Section 4.3). Even if you split by individual (good), individuals with more waves contribute more rows and may dominate model fit.

Actionable fixes:

- Weight each observation by inverse number of observations per individual.
    
- Or sample one observation per individual (e.g., closest to target age band) to create a cross-sectional training set consistent with your prediction target.
    
- Report how many unique individuals vs observations you train on and the distribution of waves per person.
    
    
    

### 12) Representativeness claims contradict your own descriptive evidence

You state respondents should be representative, but Figures 5 and 6 show differences in gender and education (Section 4.4). This directly challenges the covariate shift assumptions.

Actionable fixes:

- Use LISS survey weights if available (or discuss why not possible in RA).
    
- Provide formal covariate-shift diagnostics: standardized mean differences for key predictors between respondents and employed controls (age-stratified), not only bar charts.
    
- Consider domain adaptation / importance weighting: weight respondents during training so their covariate distribution matches the prediction target (eligible or employed). This directly addresses the “transportability” problem you emphasize.
    
    
    

## Presentation and structure improvements

### 13) Tighten the narrative: decide whether the thesis is (A) a policy evaluation or (B) a methodological cautionary study

As written, it tries to be both. Given how central and fragile the nondifferentiality assumption is, you should choose a primary contribution:

Option A (policy-focused):

- You must repair identification as much as possible (overlap validation, time alignment, no leakage, uncertainty).
    
- Then conclusions about targeting can be defended.
    

Option B (methods-focused):

- Frame the thesis as: “With only administrative covariates and predicted survey proxies, evaluation is highly sensitive to unverifiable assumptions; here is a framework and robustness bounds.”
    
- Then the main output is Figure 8-style partial identification and guidance, not point estimates.
    

Right now you present point estimates and then effectively retract confidence later, which can frustrate readers.



### 14) Clarify Table 5 and the odds ratio comparisons

Table 5 is ambiguous: it is not immediately clear which control group (employed vs eligible) each $\hat{\Psi}$ refers to, and how $\hat{\alpha}_{1,\cdot}$​ is paired with the correction choice.

Actionable fix:

- Split into two tables or add explicit columns:
    
    - $\hat{\alpha}_1$ (exempted)
        
    - $\hat{\alpha}_0$​ (employed control) and $\hat{\Psi}$ vs employed
        
    - $\hat{\alpha}_0$ (eligible control) and $\hat{\Psi}$ vs eligible
        
- Add confidence intervals (even if approximate).
    

### 15) Improve figure readability and interpretability

Figures 5–8 are doing heavy lifting but need stronger captions and in-text interpretation:

- Add sample sizes per group in captions.
    
- Ensure axis labels and legends are legible in print.
    
- For Figure 8, explicitly describe what regions are plausible given the observed $\hat{X}$ prevalence (you hint at this, but it should be operationalized).
    

## Detailed technical and writing corrections (high value, easy fixes)

### Critical typos / placeholders

- Page 5: “(toevoegen)” is a placeholder that must be removed and replaced with a citation or calculation.
    
    
- Page 10: “practice.ments for the …” indicates a broken sentence. Fix the paragraph; it currently reads as corrupted text.
    
    
- Page 27: “full unemployed population” should be “employed population” (context is comparison group (3)).
    
    
- Acknowledgements page 3: missing space “thesis.In particular,”.
    
    
- Bibliography: “werzaamheden” should be “werkzaamheden” (TNO reference).
    
    

### Notation and referencing consistency

- Section 3.1: you refer to Table “1e” for $\alpha$, but $\alpha$ corresponds to $P(X\mid Y)$, which is Table 1(d), not 1(e).
    
    
- Use consistent notation for counts: the dotted/double-dotted notation is hard to parse and easy to mistype. Consider a simpler subscript notation:
    
    - $n_{xy}​$, $n_{\hat{x}y}$​, $n_{\hat{x}xy}$​
        
- In Section 5.3 you say you weight classes so each group (Y=1 and Y=0) has equal weight. You are predicting X, not Y. This should be “each class X=1 and X=0.”
    
    
- Several figure captions and sentences have incomplete fragments (Figure 4 caption: “When true X is unknown,.”).
    
    

### Language and tone

- Reduce repetitive “We hypothesise” phrasing. In a thesis, frequent “hypothesise” without testable hypotheses can read as speculative. Use:
    
    - “We expect”, “We argue”, “This implies”, or provide explicit, testable hypotheses and test them.
        
- Avoid “Where …” constructions (“Where these studies do provide…”) that read unnatural in English. Replace with “While …”.
    

## Concrete revision checklist (prioritized)

1. Define the estimand properly and rename “efficiency” to “targeting” unless you add cost/benefit components.
    
2. ~~Fix the nondifferential misclassification statement (Eq. 5) and audit the surrounding logic.~~
    
3. Resolve the “irrecoverable mistakes” issue by re-running and correcting the data construction and weighting, or remove the affected results and reframe.
    
4. Align the target year definition with actual “pre-RVU” timing and remove any post-target predictors.
    
5. ~~Use the LISS–RVU overlap as an internal validation or, at minimum, as a direct diagnostic for differential misclassification.~~
    
6. Add uncertainty quantification (bootstrap or delta method) for corrected $\alpha$ and $\Psi$.
    
7. Rework the proxy set: remove or reclassify “supervisory” as demanding, and add robustness to thresholding of ordinal items.
    
8. Clean up all placeholders, corrupted sentences, and terminology errors (“unemployed”).


If you want, I can produce a marked-up, section-by-section rewrite plan (what to add/remove in each subsection and where) using your existing structure, but the items above are the main blockers to academic defensibility.