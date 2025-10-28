---
MOC:
  - "[[$Scriptie]]"
  - "[[$Data Aantekeningen]]"
tags:
  - note
  - data
about:
  - RVU gebruik
data_source: SEO
nrows:
ncols:
documentation:
inhoudelijk:
gearchiveerd:
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## Vragen

- [ ] Gaat het om RVU treffen of om gebruik van drempelvrijstelling RVU-heffing?
	- Hier komt Jellien op terug
	- Wss niet want anders zouden ze weten of t RVU is in de waarschijnlijk eerder
- [ ] Er zijn instances met jaar in (22,23), maar ook "eerder waarschijnlijk al RVU". Wat betekent dit?
- [ ] Wat betekent RVU pas in 2021 voor mensen met RVU in 2022 / 2023


## Aantekeningen

- In de RVU data staat CAO nummer, er bestaat een conversie naar meer informatieve naam
	- Jellien gaat kijken
	- Uitsplitsen mag niet vanuit microdata omdat er vaak 1 bedrijf achter cao zit
		- Modelleren mag wel, figuren exporteren niet
- JAAR kolom geeft aan welk jaar, met minimum 2021
	- Voor JAAR = 2021 geeft RVU kolom weer of het hiervoor was of niet
		- Als dit zo is, dan is het niet zeker of t een RVU is
		- Ook lastig te baseren op polis data omdat mensen ook ander/meer/minder inkomen kunnen hebben
		- Alleen er zijn ook instances met >21 en Eerder waarschijnlijk al
- ==We filteren RVU == "Eerder waarschijnlijk al" eruit!==
- ==We denken dat voorkomen in de data **niet** betekent dat ze ook gebruik maken van de drempelvrijstelling== 