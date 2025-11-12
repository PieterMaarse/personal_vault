---
MOC:
  - "[[$Scriptie]]"
tags:
  - note
date: 2025-11-10
about:
  - Ideeën over model om profession te voorspellen voor LISS mensen
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
## Stappenplan

1. [x] LISS mensen selecteren uit SPOLIS
2. [x] Target variable construeren
	1. [x] Profession opgedeeld in 3 groepen
3. [ ] Features constructen
4. [ ] Train/validation/test sample splitsen
	1. [ ] Als aparte datasets opslaan (test sample pas aan einde weer aanraken)?
5. [ ] Filter voor NAs in target
6. [ ] Eerste test voorspelmodel
	1. [ ] Paar simpele SPOLIS dingen (sector, salaris? laatste entry in SPOLIS)
	2. [ ] Simpel model (multinomial logit)
7. [ ] Eerste Evaluatie
	1. [ ] accuracy, precision, recall


## Design

- Target variable:
	- Profession (2020)
	- 3 levels:
		- Supervisory
		- Manual
		- Mental
	- For people who appear mutliple times, last value
- Features:
	- SPOLIS variables (jan 2020)
		- Last time they appear 
			- ==Should later be in the year of the corresponding LISS!!==
		- Multiple contracts: take one with highest basisloon
	- All changed to categorical variables
- NAs
	- LISS not in SPOLIS
		- No features to use for prediction
		- Remove
	- SPOLIS not in LISS
		- Predict
	- target
		- Filter
		- Bias?


## Checken

- [ ] Of ik de laatste selecteer chronologisch of de eerste
- [ ] Heeft SARBEIDSRELATIE ooit we waardes?
- [ ] Do profession changes correspond to contract changes? Or BASISLOON changes?
	- [ ] Hoe consistent zijn mensen met dit doorgeven? Maak tile plot van target variable
- [ ] We kunnen er een panel van maken? Alleen wel veel mensen die maar één keer voorkomen

## Ideeën

- Voorspelmodel maken voor profession voor mensen in LISS
- Menno had iets vergelijkbaars gedaan
	- [[PowerPoint EBB Voorspellingen SEO]]
- Modellen:
	- (multinomial) Logit
	- XGBoost
- Target variable: profession
	- Supervisory:
		- Higher supervisory profession
		- Intermediate supervisory profession
	- Manual work
		- Skilled and supervisory manual work
		- Semi-skilled manual work
		- Unskilled and trained manual work
		- Agrarian profession
	- Mental work
		- Higher academic or independent profession
		- Intermediate academic or independent profession
		- Other mental work
- Potential features:
	- Salary
	- Hours extra
	- Car?
	- SBI letter
	- Gewoon alles er in gooien?
	- maximum number of simultaneous contracts?
		- Collapse three or more to three+
	- ==LISS jaar moet SPOLIS jaar matchen!==
		- If someone said they have management job in 2012, take SPOLISBUS from 2012
		- Of het jaar ervoor
		- Also, if someone changes profession, this can be relevant!
		- Eerst simpel houden: gewoon de laatste pakken, wordt wss onzin.
		- Start easy? Alleen met, e.g., 2020?
	

## Vragen

- Wat te doen met meerdere contracten per persoon
	- Bij elkaar optellen?
	- Boolean voor meer dan 1?
- Wat te doen met mensen die na RVU nog gaan werken?
