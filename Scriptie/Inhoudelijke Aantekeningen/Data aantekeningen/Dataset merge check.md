---
MOC:
  - "[[$Scriptie]]"
tags:
  - note
date: 2025-11-13
about:
  - Was vermoedelijk wat fout gegaan met mergen
  - Kwamen weinig mensen van LISS voor in SPOLIS
  - Klopt wel, want veel mensen zijn oud
gearchiveerd: true
inhoudelijk: true
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---

- [x] Er zitten van de LISS dataset steeds maar 7.5k van de 13k in elk jaar van de polis. Van mensen die in 2020 in de LISS (5k) zaten er 2.8 in SPOLIS
	- [x] Mensen zitten er wel in, maar zonder bijbehorende SPOLIS data. e.g. SPOLIS_yearmonth is NA
	- [x] Klopt, want maar 2/3 is tussen de 25 en 67.
	- [x] Volgens LISS heeft maar ongeveer de helft betaald werk
- [x] Hoe kan het dat er zo veel mensen die in een bepaald jaar niet in SPOLIS zitten, maar latere jaren wel?
	- [x] Zoek uit of mensen die in 2020 in de SPOLIS zaten er het volgende jaar ook nog in zitten
	- [x] Check welke mensen er in geen enkele polis voorkomen
		- [x] Vooral oudere mensen, dat is logisch
- [x] Nogsteeds gek dat zoveel mensen niet in koppelbestand voorkomen, toch?
	- [x] Vooral van eedere jaren weinig



- LISS totaal: 18065
	- Waarvan in koppelbestand: 13433
	- Waarvan met RIN: 13061
	- Waarvan voorkomen in SPOLIS 2020-2025: 8575

- LISS 2020: 5646
	- Waarvan in koppelbestand: 5093
	- Waarvan met RIN: 4988
	- Waarvan in SPOLIS 2020: 2810
		- Ongeveer 1/3 van de mensen in LISS is onder de 25 of boven de 66
		- En net meer dan de helft van de mensen heeft paid work


- Er zijn mensen in de LISS dataset die niet voorkomen in het koppelbestand
	- Terwijl die juist als NA zouden moeten voorkomen
	- Ik heb 18065 mensen in de LISS, maar koppelbestand heeft maar 17003


- Voor LISS_year 08 moet het een string zijn om te koppelen!
- Van 2008 komen er maar 4242 van de 6951 voor in de koppel



2020:
- Mensen in de SPOLIS:  9,145,153
	- Waarvan met RINS R: 8,981,989
	- 