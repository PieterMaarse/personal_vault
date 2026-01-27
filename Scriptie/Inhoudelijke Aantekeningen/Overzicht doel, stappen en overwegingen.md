---
MOC:
tags:
  - note
date: 2026-01-23
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

## Doel

Evalueren
$$P(X = 1 | Y = 1)$$
en 
$$P(X = 1 | Y = 1) \ vs \ P(X = 1 | Y = 0)$$

However, we do not know X for people with Y = 1.


## Schattingen


We evaluate $$P(\hat{X} = 1 | Y = 1)$$


## Stappen

1. Data cleanen

2. Selecteer mensen / filter data
	- RVU/RVU_like, LISS/random
	- Wat zijn criteria?
		- Voorkomen in SPOLIS?
		- RVU mensen ook filteren voor voorkomen in SPOLIS 20?
	- Waarom?
		- Vrijwel alle RVU mensen komen voor in SPOLIS
		- SPOLIS zijn grootste predictors

3. Plotjes maken / mensen filteren
	- Welke mensen willen we houden?
	- Wat zijn de verschillen per groep?
	- Hoe verschillen de antwoorden op vragen per groep?

4. Features maken
	- Welke dingen zijn belangrijk

5. Predictions maken
	- Waar hangt het van af?
	- Voor jaar 2020
	- Hoe goed zijn de schattingen?
	- Verschilt het per groep?
	- 

6. Evaluatie
	- Nog kloten met gewichten?