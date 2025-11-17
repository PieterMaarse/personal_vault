---
MOC:
  - "[[$Scriptie]]"
  - "[[$Data Aantekeningen]]"
tags:
  - note
  - data
about:
  - LISS survey, all waves combined
data_source: CentERdata
nrows:
ncols:
documentation: "[[LISS Codebook WorkSchooling 2021]]"
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


## Aantekeningen

#### Samenvoeg proces

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

Mensen geven aan geen baan de hebben maar hebben dat wel volgens de household data en andersom

Dat is best lastig mee werken

## Profession

- Profession:
	- Kan ook zijn wat je vroeger had! Laatste functie
	- Relatie tussen profession en primary occupation is wel raar
		- Er zijn mensen die aangeven voor het huis te zorgen, maar toch een management functie te hebben?
		- Zijn dat mensen die niet meer werken?