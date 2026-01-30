---
MOC:
tags:
  - note
date: 2026-01-27
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
## Intro

Geen

## Background

geen


## Theory



## Data

Allen:
- Hoe goed koppelt de data
- Zijn het random samples
- Per sample: hoeveel komen er voor in LISS?

#### SPOLIS

#### RVU

- Welke stappen zijn belangrijk?
	- Koppelen
		- Hoeveel mensen koppelen? Hoeveel niet? Is dat random sample?
	- Random sample
		- Zijn de groepen een random sample gegeven Leeftijd / gender / sector?
	- Voor / na selecteren?

#### RVU

- Population plots
- Wie maken gebruik van RVU? Data over zwaar werk ontbreekt hierin
	- Leeftijd
	- Opleiding
	- Sector

#### LISS

- Wie hebben de survey ingevuld
	- Leeftijd / ?
- Wat zijn de antwoorden op de vragen

- Specifiek LISS kan extern maar met microdata moet nu


- Stukje over "RVU_like" en "random" samples?


## Prediction model

#### Modellen

Geen

#### Features

- Overzicht features
- Relatie features met age?

#### Training & Tuning

Geen

#### Test set performance

- Test set predictions?
- Performance tables
	- TP/FP/TN/FN (niet voor allemaal)
	- Sensitivity, specificity
	- Best model

#### Estimating Se/Sp

- Se/Sp van model over verschillende leeftijden (/ en andere features)



## Evaluation

- Plots / tables
	- Se/Sp
		- Meerdere schattingen
		- Oftewel, contingency tables voor meerdere subsets?
	- Fractions \hat{Y}
	- (de rest kunnen we daarmee berekenen? check dit!)



# Plots

- [ ] RVU
	- [ ] How many people link?
		- [ ] Is this a random sample?
	- [x] Plot that almost everyone was in SPOLIS in 2020?
	- [x] What groups are overrepresented?
		- [x] Age
		- [x] SSECT
		- [x] OPL
		- [x] Compared to:
			- [x] Random sample from 2020
			- [x] Random sample from GBA? Nee zinloos
			- [x] Random sample with same age distribution

- [x] LISS
	- [x] How many individuals merge
	- [x] When were questions answered?
	- [x] How many times do people appear?
	- [x] Is it a random sample of the working population?
		- [x] Look at one year (2020), or each year separately, not together
			- [x] Age
			- [x] Sector
			- [x] Opleiding
		- [ ] Or for every LISS year, filter for equal number of individuals who appear in that SPOLIS

- [ ] Preliminary analysis
	- [ ] Welke mensen zijn oververtegenwoordigd in RVU? (mag niet als export)
	- [ ] Welke relaties zien we tussen antwoorden op vragen en features?
	- [ ] Welke mensen zijn oververtegenwoordigd in overlap?
	- [x] Hoeveel mensen komen voor in OPL, evt naar leeftijd

- [ ] Feature gegevens?
	- [x] Zeros and NA?
	- [x] Correlations between features
	- [ ] Number of individuals in each set (train/val/test/pred)

- [x] Prediction performance
	- [x] Per vraag
	- [x] Confusion matrices test set
		- [x] Totaal
		- [x] Subgroep leeftijd
			- [x] Meerdere subgroepen om later mooie plotjes te maken
			- [ ] Of zoiets als Menno
	- [x] Predictie totalen
		- [x] Hoeveel in welke groep voor elke vraag
	- [x] Probability:
		- [x] Aantal mensen fout/goed in elke 0.10 window
	- [x] Eventueel
		- [x] Voor RVU_like zou vergelijkbare age genoeg moeten zijn



- [ ] Niet meer doen
	- [ ] Betere inschatting voor RVU Se/Sp door gewogen gemiddeldes van afstand / importance? Kan dat op basis van de procenten?
	- [ ] Prediction performance op test zet uitzetten naar LISS jaar
	- [ ] Beter kijken welke groepen goed/slect voorspellen op test set
	- [ ] Correlations with target variables?
