---
MOC:
tags:
  - note
date: 2026-01-16
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

Prio
- [ ] Andere objective:
	- [ ] ROC AUC
		- [ ] Voor trainen
	- [x] PR AUC: nee, meer focus op precision
	- [x] logloss: nee, meer focus op calibration
- [x] Youden's J voor threshold
	- [x] TPR + TNR -1 = TPR - FPR
	- [ ] In welke stap bepalen? Model selecteren op basis van auc of J?
- [x] TNR / TPR berekenen en opslaan
- [ ] Opslaan feature set als .rds
- [ ] Betere schatting voor fouten
	- [x] Eerst voor alleen leeftijd/gender
	- [ ] Daarna voor alle features
		- [ ] met gewicht = importance voor elke variabele?
		- [ ] Schatting op basis van de "closest" features, waar afstand over feature as is ( verschil / sd(feature) ) / importance(feature)?
- [ ] Figuur met fout rate per probability schattingen
- [ ] CV toevoegen
- [ ] Code aanpassen om test set echt te gebruiken

ER GAAT IETS FOUT MET RINS, sommige RINS komen vaker voor in ind_features
code herstructureren:
1. RIN file maken met RVU, LISS, random RVU_like, random random
	1. Denk na over wat ik met duplicates doe (zorg dat individuen maar in 1 groep voorkomen)
2. Haal voor die RINs de POLIS data en GBA data op, sla die op in nieuw bestand
	


- [x] Bepalen welke maatstaf ik wil gebruiken
	- [x] Beginnen met simpele kans
		- [x] $\alpha_1 = P(X=1 | Y=1)$
- [x] Naïeve berekening doen
	- [x] Hoe die direct wordt waargenomen, gewoon ratio's
- [x] Onder nondifferentiality assumption formule uitrekenen
	- [x] $\hat{\alpha}_y ​= \frac{ \alpha_y −P(W=1∣X=0) }{ P(W=1∣X=1) ​− P(W=1∣X=0)​ } = \frac{\alpha_y​−(1−Sp)​}{Se+Sp−1}$.
	- [x] Zowel met direct waargenomen als met voorspellingen op test set?
	- [ ] Of op random sample?
- [x] Robustness berekeningen doen voor andere Se/Sp
	- [x] Alleen voor Y=1 veranderen
- [x] Plotje maken
	- [x] Se/Sp op de x/y as en de maatstaf (alpha / odds ratio) als waarde
	- [x] nondifferential waarde als punt erin
- [ ] Betere inschatting proberen te maken van Se/Sp op basis van vergelijkbare sample in train set
	- [ ] Punt toevoegen aan de plot
- [x] Daarna odds ratio
	- [x] P(X = 1 | Y = 1) vs P(X = 1 | Y = 0)
		- [ ] Waarbij tweede op basis van training sample the schatten is (of op basis van random sample)
	- [ ] Of een van:
		- [ ] P(Y=1 | X=1) vs P(Y=0 | X=1) 
		- [ ] P(X=1 | Y=1) vs P(X=0 | Y=1)
- [x] Ipv punt voor nondifferentiality, een lijn gebasseerd op verschillende waarden voor threshold? Lastig want dan moet ik ook voorspellingen veranderen, wat de plot weer beinlvoedt


1. P(X=1 | Y=1)
	1. Se / Sp berekenen op training sample
	2. naïeve $\alpha_1$ berekenen voor RVU sample
	3. $\hat{\alpha}_1$ berekenen voor RVU sample
	4. $\hat{\alpha}_1$ berekenen voor verschillende Se/Sp specificaties
2. Odds ratio
	1. Voorspellingen maken voor random random sample
	2. Naïeve $\alpha_0$ vs naïeve $\alpha_1$
	3. $\hat{\alpha}_0$ met Se/Sp zoals op training sample (zal hiervoor wel representatief moeten zijn)
	4. $\hat{\alpha}_1$ veranderen en constant houden voor y=0, plotje maken


Aanpassen eerdere code:
- [ ] Voorspellingen maken voor RVU gebruikers en random sample
	- [x] Checken of ik juiste variabelen in model kneiter voor pred_set
	- [x] target = -1??
	- [ ] Voorspellingen ook maken voor random sample?
- [ ] Andere objective in training
- [ ] Sensitivity & specificity berekenen en opslaan
  



Daniël zegt ook regressie doen
- $Y = \alpha + \beta 1_{zwaar werk}$
- Dit doen in een logit regression??
- Waarbij 1 ook vervangen kan worden door expectation / kans dat
- Duidelijk maken welke aannames je doet!
- Als ik dit niet doe duidelijk uitleggen waarom niet! Maakt Daniël blij denk ik

$$\hat{\alpha}_y ​= \frac{ \alpha_y −P(W=1∣X=0) }{ P(W=1∣X=1) ​− P(W=1∣X=0)​ } = \frac{\alpha_y​−(1−Sp)​}{Se+Sp−1}$$
