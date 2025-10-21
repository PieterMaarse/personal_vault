---
MOC:
  - "[[$Scriptie]]"
tags:
  - note
date: 2025-10-07
about:
  - Overzicht en vragen omtrent de gebruikte LISS en microdata data
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
### [[RVU]]

#### Vragen

- [ ] ==Gaat het om RVU treffen of om gebruik van drempelvrijstelling RVU-heffing?==
	- Hier komt Jellien op terug
- [ ] Er zijn instances met jaar in (22,23), maar ook "eerder waarschijnlijk al RVU". Wat betekent dit?

#### Aantekeningen

- In de RVU data staat CAO nummer, er bestaat een conversie naar meer informatieve naam
	- Jellien gaat kijken
	- Uitsplitsen mag niet vanuit microdata omdat er vaak 1 bedrijf achter cao zit
		- Modelleren mag wel, figuren exporteren niet
- JAAR kolom geeft aan welk jaar, met minimum 2021
	- Voor JAAR = 2021 geeft RVU kolom weer of het hiervoor was of niet
		- Als dit zo is, dan is het niet zeker of t een RVU is
		- Ook lastig te baseren op polis data omdat mensen ook ander/meer/minder inkomen kunnen hebben
		- ==Alleen er zijn ook instances met >21 en Eerder waarschijnlijk al==


---
### Microdata

Relevante bestanden:
- Hoogsteopleidingstab: hoogste opleidingsniveau
- SPOLIS: lonen enzo
- BETAB:


#### [[HOOGSTEOPLTAB]]

- Onderwijs -> HOOGSTEOPLTAB
- Informatie over de hoogste opleiding die mensen hebben gehaald
- Dit halen ze van DUO
- Voor sommige oudere mensen mist dit
	- Dit is dan aangevuld vanuit EEB oid
- Onderwijs


#### [[SPOLIS]]

- SPOLIS -> SPOLISBUS
- [[spolisbus.pdf]]
- SPOLIS vanaf 2013
	- Daarvoor POLIS (vanaf 2006)
	- Veelal hetzelfde, maar wat kleine veranderingen
- Groot bestand, alleen eerste paar regels/relevant variabelen laden
- spolisbus.docx: documentatie over alles wat er in zit
- BEID indicatie bedrijfsniveau (versleutelde KvK)
	- Kopellen via BETAB
	- SBI op 5 digits
- Als ik met polis data iets ga doen er 9x9 staat dan is ie missing
	- Filteren oid?
- Kijken wat relevant is om e.g. management functie te voorspellen
	- Auto van de zaak
	- Bonus


#### [[BETAB]]

- KvK is omgezet naar BEID, koppelen via BETAB
- Arbeid -> BETAB
	- Onze eigen RVU data gaat tot 2023
	- Die van 2025 is te nieuw
- Hier staat SBI code
	- Koppelbestand nodig voor achterliggende betekenis van SBI
	- utilities -> code_listings -> bedrijfsindeling -> even kijken
		-  -> gebruik die van 2008?
		- Koppel sector code naar sector naam

#### EBB

- Eventueel nog nuttige info?


---
### [[LISS]]

Samenvoegen
- ER_age heeft twee dingen
	- 5 mensen geven aan op 67+ jaar early te retiren
	- Ook iemand die zegt op 8-jarige leeftijd te retiren
	- Die knikker ik er uit
- Age heeft 2009 los
- Percentage disabled was tot 20.. een eigen ingevuld getal, daarna was het 4 groepen voor (e.g. 15-30%), die eerste vertaald naar de tweede
- 2019 early retirement (ER_bool) andere vraag? Veel mensen hebben dan nee ingevuld waar andere jaren wel? Ook 24 veel mensen opeens niet
- Highest edu mist vaak voor 2019? Klopt




#### Individuele variabelen

Zie aantekeningen over specifieke vragen bij [[LISS Codebook WorkSchooling 2021]]

- ISCO 08
	- Gaat over beroepen
	- Alleen vanaf 2020
	- Afgeleid van vraag 085
	- Maar 18k van de 97k hebben hier een waarde voor
	- Vooral voor beschrijvende statistiek, te weinig overlap om te modelleren


**Onderzoeken**

- [x] Hoelang blijven mensen in de panel?
	- [x] Histogram van aantal keer dat iemand voorkomt
	- [ ] Verschilt dit per leeftijd? Scatterplot? Eerste of laatste leeftijd?

Pick one year:
- [x] What percentage NA of each column
- [x] Histogram of distribution table for relevant columns
	- [x] Distribution of age
	- [x] Distribution of groups?
		- [x] Hoeveel mensen doen zwaar werk
		- [x] Hoeveel mensen (percentage) in welke sector?
		- [x] Hoeveel mensen met pensioen?
		- [x] Hoeveel mensen disabled
		- [x] Percentage disabled per jaar

#### Meerdere variabelen


**Relevante variabelen**
- Early retirement:
	- ER_bool (99 yes)
	- ER_age
	- ER_poor_health
- Zwaar werk:
	- job_phys_demand_agree
	- disabled_bool
	- job_lift_heavy
	- job_phys_demand_often
- Alleen voor pension_bool = yes, or prim_occup = pensioner?


Leeftijd van mensen met ER_bool = True is reletief jong, duidelijke piek bij 67

#### Vragen

- [ ] Zijn mensen die vaker meedoen ouder? (ongeacht RVU)
- [ ] Verband tussen mean_age over de jaren en variabelen (nieuw afgeleide avg_age)
- [x] Duidelijk meer RVU usage bij supervisory dingen, wat gebeurt als je de niet RVU selecteert naar leeftijd? Het kan zijn dat oudere mensen gewoon meer supervisory dingen hebben en meer van RVU gebruik maken?
- [x] Wat zat er nou in LISS over werk categoriën


- [x] Welke vragen in welk jaar?
	- [x] Hoe is dit goed weer te geven?
		- [x] scatterplot met jaar op x-as, vraag op y-as en bolletje voor tenminste één niet NA
- [x] Zijn mensen die aangeven ER te pakken ook allemaal occupation retired?
- [ ] Welke groepen zijn verbonden aan zwaar werk?
	- [ ] Hoe definieer je zwaar werk?
- [ ] Zijn mensen die aangeven zwaar werk te hebben gehad eerder/meer met pensioen gegaan?
	- [ ] Bijvoorbeeld physically demanding (q416) vs disabled (...)
- [x] What questions were in what surveys
- [ ] 291-307 kan belangrijk zijn
- [ ] Do working_box and working_self coincide?
