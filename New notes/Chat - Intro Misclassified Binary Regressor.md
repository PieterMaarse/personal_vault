---
MOC:
  - "[[$Scriptie]]"
tags:
  - note
date: 2025-12-15
about:
  - Introductie met relevant papers en dingen om rekening mee te houden van Chat
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

- Measurement error in binary: misclassified binary regressor (rather than continuous measurement error)
- regression with a misclassified binary regressor
- Je zou moeten kunnen adjusten ervoor
- Papers:
    - Identifying the effect of a mis-classified, binary, endogenous regressor — shows that under misclassification (and possibly endogeneity) the regression parameter may not be point-identified; derives identified set under weak assumptions, and point identification under stronger moment conditions. [arXiv+1](https://arxiv.org/pdf/2011.07272.pdf?utm_source=chatgpt.com "https://arxiv.org/pdf/2011.07272.pdf?utm_source=chatgpt.com")
    - Correcting for Misclassified Binary Regressors Using Instrumental Variables — proposes estimators when one has a discrete instrument, even allowing misclassification rates to vary across instrument values. [Taylor & Francis Online+1](https://www.tandfonline.com/doi/pdf/10.1080/07350015.2024.2415102?utm_source=chatgpt.com "https://www.tandfonline.com/doi/pdf/10.1080/07350015.2024.2415102?utm_source=chatgpt.com")
    - The measurement-error summary in Measurement Error Models — provides general background on measurement / misclassification error in regressors. [Wikipedia+1](https://en.wikipedia.org/wiki/Errors-in-variables_model?utm_source=chatgpt.com "https://en.wikipedia.org/wiki/errors-in-variables_model?utm_source=chatgpt.com")
    - Regression with a Mis‑classified Binary Regressor: Correcting for the Hidden Bias — discusses additional bias when misclassification correlates with other regressors, and outlines correction methods under certain assumptions. [nguimkeu.com](https://www.nguimkeu.com/wp-content/uploads/2020/10/hiddenbiasv4.pdf?utm_source=chatgpt.com "https://www.nguimkeu.com/wp-content/uploads/2020/10/hiddenbiasv4.pdf?utm_source=chatgpt.com") 


Deze is belangrijk: Regression with a Misclassified Binary Regressor: Correcting for the Hidden Bias


Even a seemingly “good” classifier (in overall accuracy or AUC) may still produce systematic misclassification that biases effect estimates. Literature on misclassification bias (or “regression with misclassified binary regressors”) emphasises these rates explicitly. [files.eric.ed.gov+2nguimkeu.com+2](https://files.eric.ed.gov/fulltext/ED609299.pdf?utm_source=chatgpt.com "https://files.eric.ed.gov/fulltext/ed609299.pdf?utm_source=chatgpt.com")


- If the misclassification is **non-differential** (i.e. FP/FN rates are independent of the outcome error term and other covariates), then under certain conditions you may be able to correct for bias if FP/FN rates are known. [files.eric.ed.gov+1](https://files.eric.ed.gov/fulltext/ED609299.pdf?utm_source=chatgpt.com "https://files.eric.ed.gov/fulltext/ed609299.pdf?utm_source=chatgpt.com")
- If misclassification rates vary systematically with covariates or the instrument (in IV settings), that complicates identification and correction. [Taylor & Francis Online+1](https://www.tandfonline.com/doi/pdf/10.1080/07350015.2024.2415102?utm_source=chatgpt.com "https://www.tandfonline.com/doi/pdf/10.1080/07350015.2024.2415102?utm_source=chatgpt.com")


Assumptie van uncorrelated misclassification error met andere covariates is relevant! 

Checken of misclassification independent is van andere variabelen 

Uitzoeken: bias-adjusted regression