---
MOC:
  - "[[$Scriptie]]"
tags:
  - meeting
meeting_with:
  - Jellien Knol
date: 2025-10-21
discussed:
  - Waar microbestanden staan en wat ik er aan kan hebben
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## Te bespreken

- [x] ISCO08
- [x] Bestanden in microdata

## Aantekeningen

**ISCO 08**

- Gaat over beroepen
- Alleen vanaf 2020
- Afgeleid van een andere vraag
- Maar 18k van de 97k hebben hier een waarde voor
- Vooral voor beschrijvende statistiek, te weinig overlap om te modelleren



**Microdata**

- Belangrijkste voorspellers lijken management vs arbeid en sector (voornamelijk publiek)
- Niet kopieren naar eigen schijf
- TAB vs BUS
	- TAB: voor iedereen een versie
	- BUS: wordt geüpdatet, soort expanding window?

- Wat zit er in de microdata?
	- HOOGSTEOPLTAB
		- hoogste opleidingsniveau
	- SPOLIS
		- variable BEID (bedrijfsindicatie)
		- koppelen aan ander bestand
		- SBI op 5 digits
	- RVU
		- Geüpload door SEO


RVU:
- In de RVU data staat CAO nummer, er bestaat een conversie naar meer informatieve naam
	- Jellien gaat kijken
	- Uitsplitsen mag niet vanuit microdata omdat er vaak 1 bedrijf achter cao zit
		- Modelleren mag wel, figuren exporteren niet
- Wat bekent de jaar kolom in RVU?
	- JAAR kolom geeft aan welk jaar, met minimum 2021
	- Voor JAAR = 2021 geeft RVU kolom weer of het hiervoor was of niet
		- Als dit zo is, dan is het niet zeker of t een RVU is
		- Ook lastig te baseren op polis data omdat mensen ook ander/meer/minder inkomen kunnen hebben


HOOGSTEOPLTAB: 
- Onderwijs -> HOOGSTEOPLTAB
- Informatie over de hoogste opleiding die mensen hebben gehaald
- Dit halen ze van DUO
- Voor sommige oudere mensen mist dit
	- Dit is dan aangevuld vanuit EEB oid
- Onderwijs


SPOLIS:
- SPOLIS -> SPOLISBUS
- SPOLIS vanaf 2013
	- Daarvoor POLIS (vanaf 2006)
	- Veelal hetzelfde, maar wat kleine veranderingen
- Groot bestand, alleen eerste paar regels/relevant variabelen laden
- spolisbus.docx: documentatie over alles wat er in zit
- BEID indicatie bedrijfsniveau (versleutelde KvK)
	- Kopellen via BETAB
- Als ik met polis data iets ga doen er 9x9 staat dan is ie missing
	- Filteren oid?
- Kijken wat relevant is om e.g. management functie te voorspellen
	- Auto van de zaak
	- Bonus


BETAB:
- KvK is omgezet naar BEID, koppelen via BETAB
- Arbeid -> BETAB
	- Onze eigen RVU data gaat tot 2023
	- Die van 2025 is te nieuw
- Hier staat SBI code
	- Koppelbestand nodig voor achterliggende betekenis van SBI
	- utilities -> code_listings -> bedrijfsindeling -> even kijken
		-  -> gebruik die van 2008?
		- Koppel sector code naar sector naam


