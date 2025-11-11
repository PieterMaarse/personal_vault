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
## TODO

1. [ ] LISS mensen selecteren uit SPOLIS
2. [ ] Target variable construeren
	1. [ ] Profession opgedeeld in 3 groepen
3. [ ] Train/validation/test sample splitsen
	1. [ ] Als aparte datasets opslaan (test sample pas aan einde weer aanraken)
4. [ ] Eerste test voorspelmodel
	1. [ ] Paar simpele SPOLIS dingen (sector, salaris? laatste entry in SPOLIS)
	2. [ ] Simpel model (multinomial logit)
5. [ ] Eerste Evaluatie
	1. [ ] accuracy, precision, recall

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
