---
MOC:
tags:
  - TODO
date:
gearchiveerd:
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## TODO



Overig



- [x] Andere target variables toevoegen
	- [x] Zware dingen tillen
	- [x] Snachts werken

- [ ] Split functies naar dataset maken en model trainen
- [ ] Maak makkelijker om verschillende featuresets te testen

- [ ] Toevoegen
	- [ ] CV
	- [ ] Opslaan resultaten
	- [ ] Kijken welke niet / minder relevant zijn


- [ ] Checken
	- [ ] Zijn polis / LISS combinaties logisch?
		- [ ] Als mensen zeggen voor het laatst in een bepaald jaar te hebben gewerkt, verdwijnen ze daarna ook uit POLIS?
			- [ ] Filter voor mensen die year_stopped hebben in 2010-2024
			- [ ] Maak variabele voor jaar/maand verschil met year_stopped
				- [ ] Is er een maand_stopped?
			- [ ] Selecteer jaar voor, jaar van, jaar na
			- [ ] Kijk of er een verandering in zit in die periode
	- [ ] Of het aantal observations in train/val/test klopt?
		- [ ] Zijn er bij het omzetten naar functional een aantal verdwenen?
		- [ ] Klopt het aantal RINs?
	- [ ] Heb ik correct hoogsteopltab toegevoegd?
		- [ ] Checken hoe goed ie koppelt
		- [ ] Hoeveel mensen hebben geen opleidingsdata?
		- [ ] En in onze leeftijdscategorie?


- [ ] Nieuwe variabelen testen
	- [ ] years diff to specific years (say -1,0,1, -5, -10)
	- [ ] Variatie tussen meerdere contracten
	- [ ] Variatie binnen het jaar?
	- [ ] Infrequent categories beter samenvoegen?
