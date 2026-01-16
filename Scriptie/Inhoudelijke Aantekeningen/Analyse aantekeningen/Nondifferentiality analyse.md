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
- [ ] Bepalen welke maatstaf ik wil gebruiken
	- [ ] Beginnen met simpele kans
		- [ ] $\alpha_1 = P(X=1 | Y=1)$
- [ ] Naïeve berekening doen
	- [ ] Hoe die direct wordt waargenomen, gewoon ratio's
- [ ] Onder nondifferentiality assumption formule uitrekenen
	- [ ] $\hat{\alpha}_y ​= \frac{ \alpha_y −P(W=1∣X=0) }{ P(W=1∣X=1) ​− P(W=1∣X=0)​ } = \frac{\alpha_y​−(1−Sp)​}{Se+Sp−1}$.
	- [ ] Zowel met direct waargenomen als met voorspellingen op test set?
	- [ ] Of op random sample?
- [ ] Robustness berekeningen doen voor andere Se/Sp
	- [ ] Alleen voor Y=1 veranderen
- [ ] Plotje maken
	- [ ] Se/Sp op de x/y as en de maatstaf (alpha / odds ratio) als waarde
	- [ ] nondifferential waarde als punt erin
- [ ] Betere inschatting proberen te maken van Se/Sp op basis van vergelijkbare sample in train set
	- [ ] Punt toevoegen aan de plot
- [ ] Daarna odds ratio
	- [ ] P(X = 1 | Y = 1) vs P(X = 1 | Y = 0)
		- [ ] Waarbij tweede op basis van training sample the schatten is (of op basis van random sample)
	- [ ] Of een van:
		- [ ] P(Y=1 | X=1) vs P(Y=0 | X=1) 
		- [ ] P(X=1 | Y=1) vs P(X=0 | Y=1)


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
	- [ ] Checken of ik juiste variabelen in model kneiter voor pred_set
	- [ ] target = -1??
	- [ ] Voorspellingen ook maken voor random sample?
- [ ] Sensitivity & specificity berekenen en opslaan
- [ ] Andere objective in training




Daniël zegt ook regressie doen
- $Y = \alpha + \beta 1_{zwaar werk}$
- Dit doen in een logit regression??
- Waarbij 1 ook vervangen kan worden door expectation / kans dat
- Duidelijk maken welke aannames je doet!
- Als ik dit niet doe duidelijk uitleggen waarom niet! Maakt Daniël blij denk ik

$$\hat{\alpha}_y ​= \frac{ \alpha_y −P(W=1∣X=0) }{ P(W=1∣X=1) ​− P(W=1∣X=0)​ } = \frac{\alpha_y​−(1−Sp)​}{Se+Sp−1}$$
