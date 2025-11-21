---
MOC:
  - "[[$Scriptie]]"
tags:
  - note
date: 2025-11-19
about:
  - 2e versie model om profession te voorspellen. Neemt meerdere jaren mee.
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

## Design

- Target variable:
	- Profession
		- Can appear in the years 2008-2024
	- 3 levels: (see [[1e Versie Voorspelmodel Profession]] voor opdeling)
		- Supervisory
		- Manual
		- Mental
- Features:
	- SPOLIS variables
	- Multiple contracts: take one with highest basisloon
	- Add variable for number of contracts
	- All changed to categorical variables

- Eerst verbinden aan profession antwoord, dan jaren verschil maken, dan vertalen naar wider


## Ideeën


Problems:
- Profession can appear multiple times per individual
	- Gapped panel data?
- Polis data can be of another year than the year the person had the profession
	- Profession question can be about previous job
		- Possible to filter out if this is the case?
		- Include boolean for this as feature?
	- Multiple years could have more information?
		- Increases in basisloon instead of level?
	- People don't appear in polis?
		- Then it must be old job
- Profession can be bullshit as it is self-reported


- Model maken, waarin we elk LISS antwoord koppelen aan elk jaar van de polis? samen met feature voor hoeveel jaar het eerder / later is?
	- Dan null/missing toevoegen als mensen niet in de polis zitten? Is ook info
	- Hoe maak je dan voorspelling per persoon?
		- Voorspelling per jaar?
	- Maak je dan extra observaties of voeg je gewoon extra features toe?
		- Oppassen voor meer features dan observaties
		- Categorical variables zijn hier lastig mee, is eigenlijk gewoon een feature per categorie
	- 2-staps model?
		- Voor elke LISS response voor elk jaar een voorspelling maken?
		- Per jaar verschil model?
			- Dan kan je ook geen veranderingen meenemen
		- Eerst voor elk jaar polis voorspelling maken voor profession antwoord.
	- Model wat op basis van tijdreeksdata gaten kan voorspellen?

- [[Longitudinal random forest]]
- Unbalanced longitudinal data
- "a longitudinal random forest or mixed-effects ML model as in Capitaine et al. and Hu et al. [arXiv+1](https://arxiv.org/abs/1901.11279?utm_source=chatgpt.com)" - ChatGPT


## Uitzoeken / checken

- [ ] Welke features kunnen gerelateerd zijn met profession?
	- [ ] Nog niet helemaal duidelijk