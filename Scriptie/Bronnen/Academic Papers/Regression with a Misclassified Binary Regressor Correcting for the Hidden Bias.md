---
MOC:
  - "[[$Scriptie]]"
tags:
  - bron
type: paper
PDF: "[[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf]]"
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

Deze paper laat zien dat je bij gebruik van een misclassified binary regressor twee soorten bias hebt: attenuation bias en een "hidden" bias, die stamt uit correlatie tussen de misclassified regressor en covariates. Deze hidden bias zou tot nog toe niet zijn opgemerkt in de literatuur.

Ze stellen een manier voor die, onder de assumptie van constante misclassification probabilities per TP/TN, consistent (maar niet unbiased?) is. Deze

Die assumptie die geldt wss niet voor mij, maar eventueel wel een goed startpunt? Testen of die assumptie gek is.

Ze stellen ook manieren voor zonder kennis van misclassification probabilities, maar dat is voor mij minder relevant.

## Vragen

- [ ] Welke aannames zijn nodig voor hun methode?
	- [ ] Misclassified binary regressor is exogeen
	- [ ] Misclassification rates zijn constant
- [ ] Hoe werkt hun methode?
	- [ ] Ze schatten de misclassification rates en gebruiken deze om te corrigeren voor de bias
- [ ] Kan ik dit gebruiken voor mijn situatie?
	- [ ] Afhankelijk van of de misclassification rates constant zijn misschien wel. Dat moet ik checken.


## Notes

- Aigner kan eventueel relevant zijn
- Conditionally constant 
	- Hoe reeëel is deze assumptie?
	- Wat is het effect een een model zo flexibel als XGBoost / RF hierop?
	- Wat is het effect als één van de twee groepen meer geclusterd wordt gesampled? Bijvoorbeeld als mensen die RVU gebruiken relatief disproportioneel uit een bepaalde sector komen?
- Kan het stuk over de bounds voor mij ook relevant zijn?
- Niet meegenomen
	- Endogeniteit van misclassified binary regressor
	- Niet-constante misclassification rates

## Highlights

> [[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf#page=2&selection=12,48,17,1|p.1:   In the multivariate setting, the issue has been treated almost exclusively with the assumption that the measurement error in the binary regressor is uncorrelated with the other regressors in the model (e.g., Aigner 1973, Bollinger 1996, Card 1996, Kane, Rouse & Staiger 1999, Black, Berger & Scott 2000).]]
> Eventueel interessant papers

> [[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf#page=2&selection=31,74,34,70|p.1:  A group of papers provide estimators for the model assuming availability of the misclassi- fication probabilities through validation data or other sources (e.g., Aigner 1973, Freeman 1984, Card 1996, Savoca 2000, Battistin, Nadai & Sianesi 2014)]]
> Papers checken!

> [[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf#page=2&selection=39,17,43,72&color=general|p.1:  All these studies assume no correlation between the auxiliary regressors (or controls) and the misclassification error in the binary regressor of interest. These methods thus correct for the misclassification bias, but may not correct for the bias stemming from a possible correlation between misclassification error and other regressors in the model (what we term the “hidden bias”)]]
> Essentie van waarom deze paper

> [[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf#page=3&selection=10,53,15,51&color=general|p.2:  t expresses the correlation between misclassification error and control variables as a function of quantities that can be obtained through sample statistics, and uses it to correct for the bias in the least squares estimator.]]
> Kan ik dit ook doen?

> [[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf#page=3&selection=16,3,18,23|p.2:  Aigner (1973) is a special case of our estimator when both the misclassified binary regressor and the associated measurement error are uncorrelated with other regressors in the model]]
> Eventueel makkelijker beginpunt?

> [[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf#page=4&selection=301,1,303,1|p.3:  operational model,]]
> Operational model, term om te onthouden

> [[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf#page=5&selection=54,1,56,51|p.4:  Savoca (2000) extends Aigner (1973)’s analysis to the case when several binary regressors are misclassifie]]
> Eventueel als we meerder binary variables tegelijk erin gooien?

> [[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf#page=7&selection=102,0,102,53|p.6:  These probabilities are assumed conditionally constan]]
> Is dit een oké assumptie om te maken? 

> [[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf#page=7&selection=113,0,115,11&color=general|p.6:  This assumption implies that the measurement error may vary with the covariates, but only through the true response, and has been made in several papers]]
> Dit kan ik als eerste aanname doen, maar klopt niet. Testen met zo'n tabel als Menno

> [[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf#page=10&selection=73,0,73,9&color=general|p.9:  Theorem 2]]
> Formulatie van de bias-adjusted least squares estimator

## PDF


![[Nguimkeu (2020) - Regression with a Misclassified Binary Regressor; Correcting for the Hidden Bias.pdf]]
%% add "<" tussen "!" en "%", Alt+r to run %%