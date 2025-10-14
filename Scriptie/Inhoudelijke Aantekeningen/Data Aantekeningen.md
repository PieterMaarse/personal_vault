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

## Vragen

### LISS

Samenvoegen
- ER_age heeft twee dingen
	- 5 mensen geven aan op 67+ jaar early te retiren
	- Ook iemand die zegt op 8-jarige leeftijd te retiren
	- Die knikker ik er uit
- Age heeft 2009 los


#### Vragen

- [x] Welke vragen in welk jaar?
	- [x] Hoe is dit goed weer te geven?
		- [x] scatterplot met jaar op x-as, vraag op y-as en bolletje voor tenminste één niet NA

#### Individuele variabelen

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

##### verbanden tussen early retirement en zwaar werk

**Relevant variabelen**
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

**Vragen**

- Zijn mensen die aangeven ER te pakken ook allemaal occupation retired?

- [ ] Welke groepen zijn verbonden aan zwaar werk?
	- [ ] Hoe definieer je zwaar werk?
- [ ] Zijn mensen die aangeven zwaar werk te hebben gehad eerder/meer met pensioen gegaan?
	- [ ] Bijvoorbeeld physically demanding (q416) vs disabled (...)
- [ ] What questions were in what surveys
- [ ] 291-307 kan belangrijk zijn
- [ ] Do working_box and working_self coincide?

Zie aantekeningen over specifieke vragen bij [[LISS Codebook WorkSchooling 2021]]