---
MOC:
  - "[[$Scriptie]]"
tags:
  - bron
type: paper
PDF: "[[hiddenbiasv4.pdf]]"
link:
author(s):
year:
title:
about:
cite:
gearchiveerd:
relevant_for:
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## Samenvatting

Deze paper laat zien dat je bij gebruik van een misclassified binary regressor twee soorten bias hebt: attenuation bias en een "hidden" bias, die stamt uit correlatie tussen de misclassified regressor en covariates.

Ze stellen een manier voor die, onder de assumptie van constante misclassification probabilities per TP/TN, consistent (en unbiased is?)

Die assumptie die geldt wss niet voor mij, maar eventueel wel een goed startpunt. 


## Notes

> [[hiddenbiasv4.pdf#page=2&selection=12,48,17,1|p.1:   In the multivariate setting, the issue has been treated almost exclusively with the assumption that the measurement error in the binary regressor is uncorrelated with the other regressors in the model (e.g., Aigner 1973, Bollinger 1996, Card 1996, Kane, Rouse & Staiger 1999, Black, Berger & Scott 2000).]]
> Eventueel interessant papers

> [[hiddenbiasv4.pdf#page=2&selection=31,74,34,70|p.1:  A group of papers provide estimators for the model assuming availability of the misclassi- fication probabilities through validation data or other sources (e.g., Aigner 1973, Freeman 1984, Card 1996, Savoca 2000, Battistin, Nadai & Sianesi 2014)]]
> Papers checken

> [[hiddenbiasv4.pdf#page=2&selection=39,17,43,72&color=general|p.1:  All these studies assume no correlation between the auxiliary regressors (or controls) and the misclassification error in the binary regressor of interest. These methods thus correct for the misclassification bias, but may not correct for the bias stemming from a possible correlation between misclassification error and other regressors in the model (what we term the “hidden bias”)]]
> Essentie van waarom deze paper

> [[hiddenbiasv4.pdf#page=3&selection=10,53,15,51&color=general|p.2:  t expresses the correlation between misclassification error and control variables as a function of quantities that can be obtained through sample statistics, and uses it to correct for the bias in the least squares estimator.]]
> Kan ik dit ook doen?

> [[hiddenbiasv4.pdf#page=7&selection=113,0,115,11&color=general|p.6:  This assumption implies that the measurement error may vary with the covariates, but only through the true response, and has been made in several papers]]
> Dit kan ik als eerste aanname doen, maar klopt niet. Testen met zo'n tabel als Menno

> [[hiddenbiasv4.pdf#page=10&selection=73,0,73,9&color=general|p.9:  Theorem 2]]
> Estimators om te gebruiken in mijn situatie?

## PDF


![[hiddenbiasv4.pdf]]
%% add "<" tussen "!" en "%", Alt+r to run %%