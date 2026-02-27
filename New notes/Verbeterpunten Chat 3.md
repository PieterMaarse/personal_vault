---
MOC:
tags:
  - note
date: 2026-02-27
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
## Highest-impact issues to address first

### 1) ~~Title and framing currently overclaim “AI-generated survey responses”~~

~~Your title (“Evaluating the RVU levy exemption using AI-generated survey responses”) strongly suggests you generated survey text/responses (for example with LLMs). What you actually do is **predict binary survey outcomes from administrative features** and then use misclassification-aware inference. That distinction matters for credibility and for how readers interpret validity and ethics.~~

~~3rd_Draft_Thesis_Pieter_Maarse-2~~

~~Concrete improvements:~~

- ~~Change phrasing everywhere from **“AI-generated survey responses”** to something like:~~
    
    - ~~“administrative-data-based prediction of survey indicators”~~
        
    - ~~“ML-imputed survey outcomes”~~
        
    - ~~“predicted demanding-work proxies”~~
        
- ~~Update the abstract’s first lines to explicitly say: _“We train supervised ML models on linked LISS-CBS data to predict survey-based demanding-work indicators for RVU users and controls.”_~~
    
    ~~3rd_Draft_Thesis_Pieter_Maarse-2~~
    
- ~~Add a short paragraph early (Introduction or Data) clarifying what “AI” means here (tree-based supervised learning) and what it does not mean (no synthetic text, no generative modeling).~~
    

### 2) Core identification target shifts mid-thesis: “year before retirement” vs “pre-exemption-era”

In the Introduction you motivate evaluating whether RVU users had demanding work “the year before they retired” and say you evaluate demanding work in **2020** because users should have been employed the year before retirement.

3rd_Draft_Thesis_Pieter_Maarse-2

  
But later you state you **do not observe the RVU year**, only “before/after January 2021”, so 2020 becomes a **generic pre-exemption baseline** rather than year-before-retirement.

3rd_Draft_Thesis_Pieter_Maarse-2

This is not a minor limitation. It changes interpretation of your estimand and what the results can claim.

Concrete improvements:

- Move the “year not available” limitation from the Data section (currently under RVU users) to the **end of Section 1.2 Procedure and problems**, and rewrite the research question and estimand accordingly.
    
- Adjust wording throughout:
    
    - Replace “before they retired” with “in 2020 (pre-exemption baseline year)”.
        
    - Replace any causal-sounding phrases with “associated with later RVU use (2021–2024)”.
        
- Consider revising the main research question to match what you can actually answer, for example:
    
    - “Are later RVU users (2021–2024) predicted to have had demanding-work characteristics in 2020 more often than comparable non-users?”  
        This keeps the policy relevance while aligning with data reality.
        

### 3) ~~A serious notation/definition error in misclassification probabilities (must fix)~~

~~In Section 3.2 you define sensitivity/specificity correctly, but then state:~~  
~~“misclassification probabilities θ1|0 = 1 − θ1|1 and θ0|1 = 1 − θ0|0”~~

~~3rd_Draft_Thesis_Pieter_Maarse-2~~

  
~~This is **incorrect indexing**. Correct relationships are:~~

- ~~θ1|0 = 1 − θ0|0 (false positive rate is 1 − specificity)~~
    
- ~~θ0|1 = 1 − θ1|1 (false negative rate is 1 − sensitivity)~~
    

~~Concrete improvements:~~

- ~~Correct those two lines and scan the remainder of the theory section for any downstream indexing consequences (especially where you interpret “misclassification probabilities” vs “correct classification probabilities”).~~
    
- ~~Add a small 2×2 mapping table (one line each) explicitly naming:~~
    
    - ~~sensitivity = P(X̂=1|X=1)~~
        
    - ~~specificity = P(X̂=0|X=0)~~
        
    - ~~FPR = P(X̂=1|X=0)~~
        
    - ~~FNR = P(X̂=0|X=1)~~  
        ~~This will prevent reader confusion and protect you against examiner pushback.~~
        

### ~~4) “Six questions” vs five questions appears inconsistent across abstract, data, and results~~

~~Abstract: “select six questions”~~

~~3rd_Draft_Thesis_Pieter_Maarse-2~~

  
~~Data section: “following six questions” but then lists (a)–(e) which are **five**~~

~~3rd_Draft_Thesis_Pieter_Maarse-2~~

  
~~Tables 3–6 also cover five.~~

~~Concrete improvements:~~

- ~~Decide whether it is five or six and make it consistent:~~
    
    - ~~If five: change every “six” to “five”, including the abstract and any later references.~~
        
    - ~~If six: add the missing item everywhere (Data description, confusion matrices, sensitivity/specificity table, evaluation results, figures).~~
        
- ~~Also fix the small internal inconsistency in Table 5 description where you refer to “agree/strongly agree to question (c)” although the agree-scale item is (b).~~
    
    ~~3rd_Draft_Thesis_Pieter_Maarse-2~~
    

### ~~5) Theoretical framework is technically strong but not reader-efficient~~

~~Section 3 contains a lot of careful material (case-control setting, misclassification correction, nondifferentiality, delta method variance, Bayesian posterior).~~

~~3rd_Draft_Thesis_Pieter_Maarse-2~~

  
~~The problem is pacing: a policy-evaluation reader may not know which parts are essential for following the empirical story.~~

~~Concrete improvements (structure, no new analysis):~~

- ~~Add a **one-page roadmap** at the start of Section 3:~~
    
    1. ~~what you observe,~~
        
    2. ~~what you predict,~~
        
    3. ~~why misclassification matters,~~
        
    4. ~~what assumption yields the benchmark,~~
        
    5. ~~what you do when relaxing it.~~
        
- ~~Consider moving some derivations (for example, the full delta-method covariance expression and the long Bayesian derivation) to an **appendix**, while keeping the key formulas and intuition in the main text.~~
    
- ~~Add an overview figure (pipeline diagram): Data sources → training set → predicted proxies → benchmark correction → robustness surfaces → Bayesian importance sampling.~~
    

## Section-by-section improvements

### ~~Abstract (page i)~~

~~Current abstract is clear but reads like a methods summary; it under-serves the results and over-serves the procedure.~~

~~3rd_Draft_Thesis_Pieter_Maarse-2~~

~~Concrete improvements:~~

- ~~Add 1 sentence with your **headline benchmark conclusion** (in plain language) and 1 sentence about **fragility** (dependence on transportability).~~
    
- ~~Replace “AI-generated survey responses” logic with “ML-predicted survey indicators”.~~
    
- ~~Make the estimand explicit (2020 pre-exemption baseline; later RVU users 2021–2024).~~
    

~~A possible rewrite skeleton (illustrative, not wordsmithing everything):~~

- ~~Sentence 1: policy + objective~~
    
- ~~Sentence 2: data constraint + prediction approach~~
    
- ~~Sentence 3: how you correct for misclassification and the key assumption~~
    
- ~~Sentence 4: headline findings (which dimensions appear overrepresented under benchmark)~~
    
- ~~Sentence 5: why uncertainty remains and what would resolve it~~
    

### Introduction (Section 1)

**Strengths:** motivation and policy context are solid; you correctly warn that targeting is not causality.

3rd_Draft_Thesis_Pieter_Maarse-2

Concrete improvements:

- Add explicit citations for factual claims that are “current policy” statements (for example the coalition change in January 2026 and the new acceleration rule), or qualify as “proposed/announced”.
    
- Tighten the research question paragraph: explicitly define what “target well” means operationally (you later use α and odds ratios, but it is not foreshadowed clearly enough).
    
- Bring forward the biggest limitation (unknown RVU year) as noted above.
    

### ~~Background (Section 2)~~

~~**Strengths:** clear step-by-step explanation of RVU, levy, exemption.~~

~~3rd_Draft_Thesis_Pieter_Maarse-2~~

~~Concrete improvements:~~

- ~~The Background can better bridge into your measurement strategy:~~
    
    - ~~At the end of 2.3, add a short paragraph explicitly mapping your chosen survey questions to TNO load fields and noting what you miss (environmental, psychosocial, cognitive). You mention this, but it would benefit from a structured mapping.~~
        
- ~~Consider a compact table: “TNO load field → LISS question proxy used → limitations”.~~  
    ~~This is purely presentation and would substantially improve readability.~~
    

### Theoretical framework (Section 3)

Key improvements beyond the definition error:

1. Clarify the case-control implication earlier  
    You correctly note that case-control prevents estimating P(Y|X).
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
      
    Consider adding one sentence explicitly stating what you _can_ estimate reliably (odds ratio, group-conditional prevalence after correction) and what you _cannot_.
    
2. Clean up notation density  
    Tables with n, ṅ, n̈ are heavy.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
      
    Concrete presentation improvements:
    

- Keep Table 1 but reduce it:
    
    - show only the 2×2 table of (X, X̂) within Y strata and define sensitivity/specificity there
        
    - move the multiple embellished count notations to appendix or footnote
        
- Ensure every symbol appears with a short verbal interpretation when first used.
    

3. Fix likely typographical issues in Bayesian section  
    In Eq. (19) the exponent on (1 − pθ) appears as “k” in your PDF text extraction; later you use (n − k) in Eq. (20).
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
      
    Even if this is a typesetting artifact, it is worth verifying in the source and correcting if needed because examiners will notice.
    
4. Strengthen the “transportability” narrative  
    Section 3.6 is central and good, but you can improve the reader’s intuition:
    

- Add a short concrete example: “If RVU users are concentrated in sectors where the model under-predicts heavy lifting, specificity/sensitivity shift; corrected α and OR move accordingly.”
    
- State explicitly whether you expect bias direction for each proxy (you do not need new analysis, just a hypothesis).
    

### Data (Section 4)

This section contains some of the most important credibility content, but one element currently weakens you unnecessarily.

1. Rewrite the long footnote about data construction mistakes (Footnote 3)  
    The footnote is candid, but the tone is too personal (“I made several mistakes… access revoked… could not be recovered”).
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
      
    Examiners may interpret this as avoidable sloppiness rather than constraints.
    

Concrete rewrite strategy:

- Move it from footnote into a short, professional “Data construction limitations” subsection (end of Section 4.4 or start of Discussion).
    
- Replace first-person admissions with objective statements:
    
    - “During sample construction, several intermediate versions were produced; due to RA access constraints and disclosure limits, not all could be fully reconciled.”
        
- Clearly state _which_ biases might result and which direction (gender stratification, weighting not accounting for population birth-year frequency, etc.), but avoid procedural details like “foosball table” style informality.
    

2. Clarify representativeness argument  
    You first repeat the LISS representativeness claim, then show respondents differ from the employed sample due to cohort-year accumulation.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
      
    Improve by explicitly distinguishing:
    

- “LISS representativeness in survey year”
    
- vs “your constructed respondent pool across 2008–2024 linked to 2020 employment register”.
    

A single paragraph that explains the mismatch will pre-empt criticism.

3. Tighten definitions of the four groups  
    The 4-group setup is good.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
      
    Add one sentence explicitly stating:
    

- which groups are used for training/testing
    
- which are purely prediction targets
    
- why some overlap is handled the way you choose
    

### Predictions (Section 5)

**Strengths:** methodological choices are defensible; threshold selection aligns with your sensitivity/specificity emphasis.

3rd_Draft_Thesis_Pieter_Maarse-2

Concrete improvements:

- When you say “we use many features” and that models “select important variables themselves,” add a short sentence acknowledging the risk of **dataset shift**: feature distributions differ between respondents and exempted, which is precisely your transportability concern. This links Section 5 to Section 3.6 and makes the narrative tighter.
    
- Clarify whether your unit of observation is a response-wave or a person-year. Right now the text oscillates between “responses” and “individuals,” which makes it harder to interpret the confusion matrices and test size.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
- In Table 3 and Table 4, consider adding:
    
    - prevalence in test set (share X=1)
        
    - confidence intervals for sensitivity/specificity (binomial)  
        This is presentation-level and strengthens inferential seriousness, even if you keep the later Bayesian approach.
        

### Evaluation (Section 6)

**Strengths:** you clearly separate naive prediction rates from corrected benchmark and from robustness/Bayesian relaxation.

3rd_Draft_Thesis_Pieter_Maarse-2

Concrete improvements:

1. Benchmark assumption needs to be stated more prominently at the start of 6.2  
    Currently, the reader reaches Table 5 and only gradually realizes the benchmark is a strong transportability assumption. Make the first paragraph of 6.2 explicitly say:
    

- what is assumed transportable to whom (controls vs exempted)
    
- why that is questionable
    
- what interpretation Table 5 should receive (“conditional on transportability”)
    

2. Fix small typographical/format issues that reduce professionalism  
    Examples visible in the text:
    

- “95& confidence intervals” should be “95%”.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
- Occasional encoding artifacts (for example “over￾or”) should be removed in final typeset output.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    

3. Handle negative probability confidence interval bounds more carefully  
    You note α CIs spanning negative values and attribute to delta method near boundaries.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
      
    Concrete text/presentation improvements (no new analysis needed conceptually):
    

- Explicitly state that the _parameter space is [0,1]_ and that the reported intervals are approximate.
    
- Consider reporting truncated intervals for interpretability (for example max(lower,0), min(upper,1)), while keeping the original in parentheses or in an appendix note.
    
- Alternatively, state that you interpret them as “close to zero with substantial uncertainty” rather than as literal negative probabilities.
    

4. Improve interpretation of the (b) vs (c) discrepancy  
    You call it “interesting” and later “Weirdly”.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
      
    Replace with a short conceptual explanation:
    

- (b) is a global self-assessment (“my job is/was physically demanding”) on agree-scale
    
- (c) is frequency-based (“is/was your job physically demanding?” never/sometimes/often)  
    These can capture different constructs: perceived demand vs frequent demand. This is exactly the kind of nuance policymakers need.
    

### Conclusion and discussion (Section 7)

Concrete improvements:

- Remove informal phrasing (“Weirdly”). Replace with neutral academic tone.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
- Strengthen the final takeaway by separating:
    
    1. what you find under benchmark
        
    2. what remains plausible under relaxed assumptions
        
    3. what cannot be concluded without additional validation data  
        This separation is already present but could be sharper and more explicit.
        

### Bibliography and citation style

Your references mix journal-style entries with raw government URLs and “accessed” notes.

3rd_Draft_Thesis_Pieter_Maarse-2

Concrete improvements:

- Choose one consistent style (APA/Chicago/your department’s standard) and apply it uniformly:
    
    - government documents: authoring institution, year, title, document type, stable URL, access date (if required)
        
- Fix line-break hyphenations in URLs (some appear split).
    
- Ensure every in-text claim that is not general knowledge has a corresponding citation (especially policy details, amounts, rates).
    

## Cross-cutting writing and presentation fixes (quick wins)

- Consistency in pronouns: you use “we” throughout but switch to “I” in the data-construction footnote. Standardize to one voice (usually “we” or passive academic voice) across the thesis.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
- Terminology consistency:
    
    - “RVU” vs “RVU levy exemption” vs “exemption” vs “threshold exemption”: pick one primary term and define abbreviations once.
        
- Add one “reader anchor” early:
    
    - a short paragraph listing the five proxies (irregular hours, physical demanding agree, physical demanding often, heavy lifting, kneel/stoop), what they represent (TNO load fields), and the time reference (2020).
        
- Verify that every figure and table is introduced with: what is plotted, what sample, what year, what the reader should learn.
    
- Remove duplicated text in acknowledgements (the LISS panel paragraph repeats “data were collected…”).
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    

## What I would prioritize if you have limited revision time

1. Fix the misclassification indexing error in Section 3.2 and check for any ripple effects.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
2. Resolve “six vs five questions” everywhere (abstract, data, tables, conclusions).
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
3. Align research question and interpretation with the “2020 pre-exemption baseline” reality by moving that limitation into the Introduction and rewriting claims accordingly.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
4. Professionalize and relocate the “sampling mistakes” footnote into a concise limitations subsection with neutral tone.
    
    3rd_Draft_Thesis_Pieter_Maarse-2
    
5. Retitle and reframe to avoid “AI-generated responses” ambiguity and potential credibility damage.
    
    3rd_Draft_Thesis_Pieter_Maarse-2