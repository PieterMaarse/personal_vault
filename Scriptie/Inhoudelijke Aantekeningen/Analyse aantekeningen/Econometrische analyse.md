---
MOC:
  - "[[$Scriptie]]"
tags:
  - note
date: 2025-10-07
about:
  - Aantekeningen over hoe ik de analyse wil gaan aanpakken
gearchiveerd:
inhoudelijk: true
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## Econometrische Analyse

Zie [[Scriptie Introductie 1e versie]] voor een eerste idee, [[Idee Daniël over analyse]] voor een idee van Daniel en PowerPoint in microdata voor eigen idee.

Eerste basic model:

$$P(RVU) = \alpha + \beta_1 \mathbb{I}_{\hat{Q}_{prof} = 1}+ \beta_2 + \gamma X$$

Maakt zwaar werk de kans op RVU groter of kleiner?

Stappenplan:
1. Selecteer population met vergelijkbare mensen als RVU gebruikers gebaseerd op geslacht, leeftijd, (opleidingsniveau, sector?)
	1. Maak 2 datasets: 1) met polis variabelen voor LISS mensen om model te trainen en 2) met RVU en RVU-achtige mensen
	2. Selecteer uit 2015 (?) random sample van mensen die in polis zitten. Selecteer op basis van geslacht, leeftijd
	3. Hoe doen met overlap?
2. Voorspel de profession / til vraag voor beide populaties
	1. Bereken features voor de tweede subsample
	2. Kies beste model
	3. Train model voor mensen die LISS hebben ingevuld (set 1)
	4. Voorspel voor mensen die dat niet hebben gedaan (set 2)
	5. Range aan jaren (2020-2024?)
3. Donder het in een (logistische) regressie


Problemen:
- Omitted variable bias
	- Vraag als proxy voor dingen die niet worden meegenomen
	- Sector
		- Mensen met zwaar werk eerder in sectoren die meer RVU gebruiken?
	- Salaris
		- Mensen met weinig salaris eerder RVU en vraag = 1?
- Misclassified regressor
	- Independence van error en andere variabelen
- Kans op RVU misschien niet meest belangrijk?
- Waarom die RVU_like? Is het dan makkelijker? Hebben we dan echt minder observations nodig?