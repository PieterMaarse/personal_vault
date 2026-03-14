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
## Updated to-do list that fits your constraints



### Global framing tasks

1. **Reframe the thesis as “bounds-first, point-estimates-as-benchmark.”**  
    You can still report corrected point estimates, but they should be explicitly labeled as:
    

- a **benchmark** under nondifferential misclassification, and
    
- secondary to the **identified regions/bounds** that remain valid under weaker, explicit assumptions.
    

2. **Surface the irrecoverable mistakes early, then contain them.**  
    Because you will keep the results, you need a consistent disclosure strategy:
    

- Mention once in the **Abstract** (one sentence).
    
- Explain once in **Data / Empirical design** (short, factual, no apology).
    
- Interpret consistently in **Evaluation** and **Conclusion** (results are exploratory; main claims come from robustness/bounds).
    

3. **Lock the proxy definition and binarization as part of the estimand.**  
    Since you cannot do binarization robustness, treat the binarization rule as part of what you are studying:
    

- “Demanding work proxy = indicator for often/agree/etc. on LISS item Q.”
    
- Then the limitation is: “Different thresholds correspond to different constructs; not examined.”
    

---

## Section-by-section rewrite plan

### Abstract

Add 2 sentences:

- **One sentence** that the main contribution is a **sensitivity/bounds analysis** due to unverifiable transportability of prediction errors.
    
- **One sentence** that results are **subject to known implementation limitations** in sampling/weighting that could not be repaired after data access ended.
    

Keep the benchmark results, but phrase as: “Under the benchmark assumption of nondifferential prediction errors, corrected estimates suggest …; bounds show which conclusions are robust.”

### 1 Introduction

**1.1 Motivation and research question**

- Replace “efficiency” with a **targeting** concept (definitions below).
    
- Add a paragraph that states what you can and cannot learn in a case-control design:
    
    - You estimate P(X=1∣Y=1)P(X=1\mid Y=1)P(X=1∣Y=1) and representation relative to controls.
        
    - You do not estimate take-up among demanding workers P(Y=1∣X=1)P(Y=1\mid X=1)P(Y=1∣X=1).
        

Add an “Interpretation” sentence: “We treat point estimates as benchmarks and emphasize robustness regions because key error rates are not identified for RVU users.”

**1.2 Procedure and problems**

- Convert this into a 5-step pipeline, then explicitly split assumptions into:
    
    - Assumptions for controls (more plausible),
        
    - Assumptions for RVU users (least plausible, therefore bounded).
        

### 2 Background

No structural changes required, but add one paragraph in 2.3 clarifying:

- your proxies cover only a subset of the TNO load fields, so your results are about “targeting to these measurable dimensions,” not “demanding work in full generality.”
    

### 3 Theoretical framework

Add a new subsection at the start:

**3.0 Identification vs partial identification**

- Define point identification: parameters are uniquely determined from observed data and maintained assumptions.
    
- Define partial identification: parameters are only constrained to a set (bounds/region) because some key quantities are unknown.
    

Then revise the rest to support the bounds-first story:

**3.1 Entities of interest**

- Define “targeting metrics” explicitly (see below).
    
- State clearly: the main inferential object is a set (bounds) for α1\alpha_1α1​ and for representation metrics, not only a point.
    

**3.2 Misclassification problem**

- Present the correction equation as a mapping:
    
    ay=P(X^=1∣Y=y)=αySey+(1−αy)(1−Spy).a_y = P(\hat X=1\mid Y=y)=\alpha_y Se_y + (1-\alpha_y)(1-Sp_y).ay​=P(X^=1∣Y=y)=αy​Sey​+(1−αy​)(1−Spy​).
    
    And inversion when Sey,SpySe_y,Sp_ySey​,Spy​ are known:
    
    αy=ay+Spy−1Sey+Spy−1.\alpha_y=\frac{a_y+Sp_y-1}{Se_y+Sp_y-1}.αy​=Sey​+Spy​−1ay​+Spy​−1​.
- Then immediately state: for RVU users Se1,Sp1Se_1,Sp_1Se1​,Sp1​ are not observed, so α1\alpha_1α1​ is not point identified without strong assumptions.
    

**3.4 Nondifferentiality**

- Make nondifferentiality the “benchmark assumption,” not the default truth.
    
- Introduce your practical approach: “We report benchmark point estimates under nondifferentiality and then relax it via regions for Se1,Sp1Se_1,Sp_1Se1​,Sp1​.”
    

### 4 Data

**4.4 Comparison groups**

- Add a short “Implementation limitations” paragraph that states:
    
    - there are known issues in how some samples/weights were constructed and cannot be corrected,
        
    - therefore results are interpreted as exploratory benchmarks, with the bounds/regions being the main robustness tool.
        

Do not spread this across multiple places. Put it here and refer back later.

### 5 Predictions

**5.4 Estimating sensitivity and specificity**

- Add a subsection titled **“Sampling uncertainty in SeSeSe and SpSpSp”**:
    
    - show that SeSeSe and SpSpSp are estimated from finite test-set counts,
        
    - provide formulas for their standard errors (binomial).
        

### 6 Evaluation

Restructure into 3 layers per proxy:

**Layer 1: Descriptive prediction shares**

- Report ay=P(X^=1∣Y=y)a_y=P(\hat X=1\mid Y=y)ay​=P(X^=1∣Y=y) for each group.
    

**Layer 2: Benchmark correction under nondifferentiality**

- Report corrected α^y\hat\alpha_yα^y​ and an uncertainty interval (delta method below).
    
- Report representation metric (odds ratio or risk ratio) with uncertainty.
    

**Layer 3: Partial identification via regions**

- Make Figure 8 (or an equivalent) the centerpiece:
    
    - classify each proxy as “robustly overrepresented,” “robustly underrepresented,” or “ambiguous,” relative to each control group, over your chosen plausible region for (Se1,Sp1)(Se_1,Sp_1)(Se1​,Sp1​).
        

If you cannot recompute anything: you can still do this classification visually using the existing boundary plots, but you should describe a principled region choice (next section) and be explicit that classification is based on the plotted region.

### 7 Conclusion and discussion

- Conclusions should be tiered:
    
    1. what holds robustly over regions,
        
    2. what holds only under benchmark nondifferentiality,
        
    3. what remains ambiguous.
        
- The “irrecoverable mistakes” should not be discussed as an afterthought. Refer back to the single limitation statement in Section 4 and reiterate the implication: “results are exploratory; emphasis is on robustness regions.”
    

---

## What “partially identified” means and how to use regions

### Definition in your setting

You observe (or can compute) ay=P(X^=1∣Y=y)a_y = P(\hat X=1\mid Y=y)ay​=P(X^=1∣Y=y). You want αy=P(X=1∣Y=y)\alpha_y=P(X=1\mid Y=y)αy​=P(X=1∣Y=y). They are linked by:

ay=αySey+(1−αy)(1−Spy).a_y=\alpha_y Se_y + (1-\alpha_y)(1-Sp_y).ay​=αy​Sey​+(1−αy​)(1−Spy​).

- If (Sey,Spy)(Se_y,Sp_y)(Sey​,Spy​) are known, αy\alpha_yαy​ is **point identified** by inversion.
    
- For RVU users, (Se1,Sp1)(Se_1,Sp_1)(Se1​,Sp1​) are not known and are not directly estimable, so α1\alpha_1α1​ and any representation metric are **not point identified** unless you assume transportability.
    

Instead, you specify a **plausible region** R⊂[0,1]2R\subset[0,1]^2R⊂[0,1]2 for (Se1,Sp1)(Se_1,Sp_1)(Se1​,Sp1​). Then α1\alpha_1α1​ is **set identified**:

α1∈{a1+Sp−1Se+Sp−1:(Se,Sp)∈R}.\alpha_1 \in \left\{\frac{a_1+Sp-1}{Se+Sp-1} : (Se,Sp)\in R \right\}.α1​∈{Se+Sp−1a1​+Sp−1​:(Se,Sp)∈R}.

That set is your **partial identification bound**.

The same applies to an odds ratio Ψ\PsiΨ. You compute Ψ(Se,Sp)\Psi(Se,Sp)Ψ(Se,Sp) across the region and report:

- Ψmin⁡=min⁡(Se,Sp)∈RΨ(Se,Sp)\Psi_{\min}=\min_{(Se,Sp)\in R}\Psi(Se,Sp)Ψmin​=min(Se,Sp)∈R​Ψ(Se,Sp)
    
- Ψmax⁡=max⁡(Se,Sp)∈RΨ(Se,Sp)\Psi_{\max}=\max_{(Se,Sp)\in R}\Psi(Se,Sp)Ψmax​=max(Se,Sp)∈R​Ψ(Se,Sp)
    

### How to choose the region RRR

You need something defensible and transparent. Options, from conservative to less conservative:

1. **Rectangle around benchmark estimates**  
    Let (S^e,S^p)(\hat Se,\hat Sp)(S^e,S^p) be your test-set estimate (possibly age-weighted). Choose:
    

R={(Se,Sp):∣Se−S^e∣≤δSe, ∣Sp−S^p∣≤δSp}R=\{(Se,Sp): |Se-\hat Se|\le \delta_{Se},\ |Sp-\hat Sp|\le \delta_{Sp}\}R={(Se,Sp):∣Se−S^e∣≤δSe​, ∣Sp−S^p∣≤δSp​}

with δ\deltaδ chosen to reflect plausible non-transport due to covariate shift (for example 0.05, 0.10). You justify δ\deltaδ qualitatively.

2. **Statistical uncertainty region for Se,SpSe,SpSe,Sp plus extra slack**  
    Take a confidence region for Se,SpSe,SpSe,Sp from the test set (binomial intervals), then expand it by an additional margin to allow differentiality for RVU users.
    
3. **Feasibility-restricted region**  
    Restrict to (Se,Sp)(Se,Sp)(Se,Sp) that produce α1∈[0,1]\alpha_1\in[0,1]α1​∈[0,1] given a1a_1a1​, and optionally to Se+Sp>1Se+Sp>1Se+Sp>1 (better-than-random classification).
    

### How to present “careful results” with partial identification

You can still give results, but they should be stated like this:

- **Robust sign conclusion:** If Ψmin⁡>1\Psi_{\min}>1Ψmin​>1, overrepresentation holds for all (Se,Sp)∈R(Se,Sp)\in R(Se,Sp)∈R. This is the strongest statement.
    
- **Ambiguous:** If Ψmin⁡≤1≤Ψmax⁡\Psi_{\min}\le 1 \le \Psi_{\max}Ψmin​≤1≤Ψmax​, the direction depends on which (Se,Sp)(Se,Sp)(Se,Sp) is true.
    
- **Benchmark-only:** If the benchmark point gives Ψ>1\Psi>1Ψ>1 but your plausible region crosses 1, you report it as suggestive, not conclusive.
    

This lets you mix Track A and B: you provide benchmark estimates (Track A), but your main claims are framed as robust or not across explicit regions (Track B).

---

## How to define “targeting” and research question options

### Targeting definitions you can support with your design

Let Y=1Y=1Y=1 be RVU user, X=1X=1X=1 be “in the intended group,” proxied by a LISS-based demanding-work indicator.

1. **Targeting precision (composition among users)**
    

Precision=P(X=1∣Y=1)=α1.\text{Precision} = P(X=1\mid Y=1)=\alpha_1.Precision=P(X=1∣Y=1)=α1​.

Interpretation: share of beneficiaries in the intended group.

2. **Relative targeting (representation)**  
    Compare users to a control group:
    

- Risk ratio: RR=P(X=1∣Y=1)P(X=1∣Y=0)RR=\frac{P(X=1\mid Y=1)}{P(X=1\mid Y=0)}RR=P(X=1∣Y=0)P(X=1∣Y=1)​
    
- Odds ratio: Ψ=α1(1−α0)α0(1−α1)\Psi=\frac{\alpha_1(1-\alpha_0)}{\alpha_0(1-\alpha_1)}Ψ=α0​(1−α1​)α1​(1−α0​)​
    

3. **Targeting differential (absolute difference)**
    

Δ=P(X=1∣Y=1)−P(X=1∣Y=0).\Delta = P(X=1\mid Y=1)-P(X=1\mid Y=0).Δ=P(X=1∣Y=1)−P(X=1∣Y=0).

What you cannot credibly call targeting with your sampling is **coverage**:

P(Y=1∣X=1),P(Y=1\mid X=1),P(Y=1∣X=1),

because the case-control structure blocks it without additional information.

### Research question formulations that fit your “mixed Track A/B” goal

Option A (clean and aligned):

- “To what extent are RVU users characterized by demanding-work proxies, and are these proxies robustly overrepresented among RVU users relative to employed and age-matched controls under plausible misclassification error regions?”
    

Option B (explicit about assumptions):

- “Under which assumptions on prediction error transportability can RVU usage be interpreted as targeted toward demanding work, and which dimensions remain robust when these assumptions are relaxed to regions?”
    

Option C (method-first, results included):

- “How sensitive are conclusions about RVU targeting to violations of nondifferential prediction error, and what can be inferred using partial identification bounds?”
    

---

## Adding uncertainty with the delta method under nondifferential misclassification

Below is a practical recipe that only needs summary statistics (confusion matrices and group sizes), not microdata. It matches your benchmark nondifferentiality analysis.



### Step 1: Notation and corrected prevalence

For a given group yyy:

- ay=P(X^=1∣Y=y)a_y = P(\hat X=1\mid Y=y)ay​=P(X^=1∣Y=y) is the observed predicted share.
    
- Se=P(X^=1∣X=1)Se = P(\hat X=1\mid X=1)Se=P(X^=1∣X=1), Sp=P(X^=0∣X=0)Sp=P(\hat X=0\mid X=0)Sp=P(X^=0∣X=0).
    
- Define D=Se+Sp−1D = Se+Sp-1D=Se+Sp−1.
    

Corrected prevalence:

α^y=ay+Sp−1D.\hat\alpha_y = \frac{a_y+Sp-1}{D}.α^y​=Day​+Sp−1​.

### Step 2: Variance of inputs aya_yay​, SeSeSe, SpSpSp

Use binomial approximations:

- If the group has nyn_yny​ individuals and m^y\hat m_ym^y​ predicted ones, then a^y=m^y/ny\hat a_y=\hat m_y/n_ya^y​=m^y​/ny​ and:
    

Var^(a^y)≈a^y(1−a^y)ny.\widehat{\mathrm{Var}}(\hat a_y)\approx \frac{\hat a_y(1-\hat a_y)}{n_y}.Var(a^y​)≈ny​a^y​(1−a^y​)​.

- From the test-set confusion matrix:
    
    - n1=TP+FNn_1 = TP+FNn1​=TP+FN, S^e=TP/n1\hat Se = TP/n_1S^e=TP/n1​, and
        

Var^(S^e)≈S^e(1−S^e)n1.\widehat{\mathrm{Var}}(\hat Se)\approx \frac{\hat Se(1-\hat Se)}{n_1}.Var(S^e)≈n1​S^e(1−S^e)​.

- n0=TN+FPn_0 = TN+FPn0​=TN+FP, S^p=TN/n0\hat Sp = TN/n_0S^p=TN/n0​, and
    

Var^(S^p)≈S^p(1−S^p)n0.\widehat{\mathrm{Var}}(\hat Sp)\approx \frac{\hat Sp(1-\hat Sp)}{n_0}.Var(S^p)≈n0​S^p(1−S^p)​.

Assume a^y\hat a_ya^y​ is independent of S^e,S^p\hat Se,\hat SpS^e,S^p (reasonable because group predictions and test set are disjoint). Assume S^e\hat SeS^e and S^p\hat SpS^p are approximately independent because they are computed on disjoint subsets of the test set (true X=1X=1X=1 vs true X=0X=0X=0).

### Step 3: Delta method for α^y\hat\alpha_yα^y​

Compute derivatives:

∂α∂a=1D,∂α∂Se=−a+Sp−1D2,∂α∂Sp=Se−aD2.\frac{\partial \alpha}{\partial a}=\frac{1}{D}, \quad \frac{\partial \alpha}{\partial Se}= -\frac{a+Sp-1}{D^2}, \quad \frac{\partial \alpha}{\partial Sp}= \frac{Se-a}{D^2}.∂a∂α​=D1​,∂Se∂α​=−D2a+Sp−1​,∂Sp∂α​=D2Se−a​.

Then:

Var^(α^y)≈(1D)2Var^(a^y)+(ay+Sp−1D2)2Var^(S^e)+(Se−ayD2)2Var^(S^p).\widehat{\mathrm{Var}}(\hat\alpha_y)\approx \left(\frac{1}{D}\right)^2\widehat{\mathrm{Var}}(\hat a_y) + \left(\frac{a_y+Sp-1}{D^2}\right)^2\widehat{\mathrm{Var}}(\hat Se) + \left(\frac{Se-a_y}{D^2}\right)^2\widehat{\mathrm{Var}}(\hat Sp).Var(α^y​)≈(D1​)2Var(a^y​)+(D2ay​+Sp−1​)2Var(S^e)+(D2Se−ay​​)2Var(S^p).

A 95 percent CI:

α^y±1.96Var^(α^y).\hat\alpha_y \pm 1.96\sqrt{\widehat{\mathrm{Var}}(\hat\alpha_y)}.α^y​±1.96Var(α^y​)​.

### Step 4: Delta method for the odds ratio with shared Se,SpSe,SpSe,Sp

Let:

Ψ=α1(1−α0)α0(1−α1).\Psi=\frac{\alpha_1(1-\alpha_0)}{\alpha_0(1-\alpha_1)}.Ψ=α0​(1−α1​)α1​(1−α0​)​.

Work with log⁡Ψ\log\PsilogΨ:

ℓ=log⁡Ψ=log⁡α1−log⁡(1−α1)+log⁡(1−α0)−log⁡α0.\ell=\log\Psi=\log\alpha_1-\log(1-\alpha_1)+\log(1-\alpha_0)-\log\alpha_0.ℓ=logΨ=logα1​−log(1−α1​)+log(1−α0​)−logα0​.

Derivatives with respect to α1,α0\alpha_1,\alpha_0α1​,α0​:

∂ℓ∂α1=1α1+11−α1,∂ℓ∂α0=−(1α0+11−α0).\frac{\partial \ell}{\partial \alpha_1}=\frac{1}{\alpha_1}+\frac{1}{1-\alpha_1}, \quad \frac{\partial \ell}{\partial \alpha_0}= -\left(\frac{1}{\alpha_0}+\frac{1}{1-\alpha_0}\right).∂α1​∂ℓ​=α1​1​+1−α1​1​,∂α0​∂ℓ​=−(α0​1​+1−α0​1​).

Now incorporate that α1\alpha_1α1​ and α0\alpha_0α0​ both depend on the same Se,SpSe,SpSe,Sp. Do a delta method directly in terms of (a1,a0,Se,Sp)(a_1,a_0,Se,Sp)(a1​,a0​,Se,Sp):

- ∂ℓ∂a1=∂ℓ∂α1⋅∂α1∂a1=(1α1+11−α1)1D\frac{\partial \ell}{\partial a_1}=\frac{\partial \ell}{\partial \alpha_1}\cdot \frac{\partial \alpha_1}{\partial a_1}=\left(\frac{1}{\alpha_1}+\frac{1}{1-\alpha_1}\right)\frac{1}{D}∂a1​∂ℓ​=∂α1​∂ℓ​⋅∂a1​∂α1​​=(α1​1​+1−α1​1​)D1​
    
- ∂ℓ∂a0=∂ℓ∂α0⋅∂α0∂a0=−(1α0+11−α0)1D\frac{\partial \ell}{\partial a_0}=\frac{\partial \ell}{\partial \alpha_0}\cdot \frac{\partial \alpha_0}{\partial a_0}= -\left(\frac{1}{\alpha_0}+\frac{1}{1-\alpha_0}\right)\frac{1}{D}∂a0​∂ℓ​=∂α0​∂ℓ​⋅∂a0​∂α0​​=−(α0​1​+1−α0​1​)D1​
    
- ∂ℓ∂Se=∂ℓ∂α1∂α1∂Se+∂ℓ∂α0∂α0∂Se\frac{\partial \ell}{\partial Se}=\frac{\partial \ell}{\partial \alpha_1}\frac{\partial \alpha_1}{\partial Se}+\frac{\partial \ell}{\partial \alpha_0}\frac{\partial \alpha_0}{\partial Se}∂Se∂ℓ​=∂α1​∂ℓ​∂Se∂α1​​+∂α0​∂ℓ​∂Se∂α0​​
    
- ∂ℓ∂Sp=∂ℓ∂α1∂α1∂Sp+∂ℓ∂α0∂α0∂Sp\frac{\partial \ell}{\partial Sp}=\frac{\partial \ell}{\partial \alpha_1}\frac{\partial \alpha_1}{\partial Sp}+\frac{\partial \ell}{\partial \alpha_0}\frac{\partial \alpha_0}{\partial Sp}∂Sp∂ℓ​=∂α1​∂ℓ​∂Sp∂α1​​+∂α0​∂ℓ​∂Sp∂α0​​
    

Where ∂αy/∂Se\partial \alpha_y/\partial Se∂αy​/∂Se and ∂αy/∂Sp\partial \alpha_y/\partial Sp∂αy​/∂Sp are the derivatives given above.

Then approximate:

Var^(ℓ^)≈(∂ℓ∂a1)2Var^(a^1)+(∂ℓ∂a0)2Var^(a^0)+(∂ℓ∂Se)2Var^(S^e)+(∂ℓ∂Sp)2Var^(S^p).\widehat{\mathrm{Var}}(\hat \ell)\approx \left(\frac{\partial \ell}{\partial a_1}\right)^2\widehat{\mathrm{Var}}(\hat a_1) + \left(\frac{\partial \ell}{\partial a_0}\right)^2\widehat{\mathrm{Var}}(\hat a_0) + \left(\frac{\partial \ell}{\partial Se}\right)^2\widehat{\mathrm{Var}}(\hat Se) + \left(\frac{\partial \ell}{\partial Sp}\right)^2\widehat{\mathrm{Var}}(\hat Sp).Var(ℓ^)≈(∂a1​∂ℓ​)2Var(a^1​)+(∂a0​∂ℓ​)2Var(a^0​)+(∂Se∂ℓ​)2Var(S^e)+(∂Sp∂ℓ​)2Var(S^p).

Finally:

- SE(ℓ^)=Var^(ℓ^)SE(\hat\ell)=\sqrt{\widehat{\mathrm{Var}}(\hat\ell)}SE(ℓ^)=Var(ℓ^)​
    
- 95 percent CI for Ψ\PsiΨ: exp⁡(ℓ^±1.96 SE(ℓ^))\exp(\hat\ell \pm 1.96\,SE(\hat\ell))exp(ℓ^±1.96SE(ℓ^))
    

### Step 5: How to get the needed inputs without microdata

If you do not have a^y\hat a_ya^y​ stored, you can reconstruct it from reported corrected estimates:

From α^y=ay+Sp−1D\hat\alpha_y=\frac{a_y+Sp-1}{D}α^y​=Day​+Sp−1​, solve:

a^y=α^yD−Sp+1.\hat a_y = \hat\alpha_y D - Sp + 1.a^y​=α^y​D−Sp+1.

If you also need α^0\hat\alpha_0α^0​ but only have α^1\hat\alpha_1α^1​ and Ψ^\hat\PsiΨ^, solve:

α^0=α^1Ψ^(1−α^1)+α^1.\hat\alpha_0 = \frac{\hat\alpha_1}{\hat\Psi(1-\hat\alpha_1)+\hat\alpha_1}.α^0​=Ψ^(1−α^1​)+α^1​α^1​​.

This lets you compute uncertainty intervals using only:

- the confusion matrices (for Se,Sp,n1,n0Se,Sp,n_1,n_0Se,Sp,n1​,n0​),
    
- the reported corrected α^1\hat\alpha_1α^1​ and Ψ^\hat\PsiΨ^,
    
- the group sample sizes nyn_yny​.
    
    
    

---

## How to combine “uncertainty” with “partial identification” in your narrative

You have two distinct uncertainty concepts:

1. **Sampling uncertainty** (delta method CIs): conditional on a chosen (Se,Sp)(Se,Sp)(Se,Sp) benchmark.
    
2. **Identification uncertainty** (regions/bounds): because (Se1,Sp1)(Se_1,Sp_1)(Se1​,Sp1​) for RVU users is not known.
    

Recommended presentation:

- Report benchmark point estimate + CI under nondifferentiality.
    
- Then report the partial identification region result (robust/ambiguous) over RRR.  
    This makes clear that even a very tight CI can still be policy-ambiguous if the sign flips within RRR.
    

If you want one combined statement: define the final uncertainty set as the union of CIs across (Se,Sp)∈R(Se,Sp)\in R(Se,Sp)∈R, but that requires additional computation (still feasible outside the CBS environment if you have the needed summary inputs).