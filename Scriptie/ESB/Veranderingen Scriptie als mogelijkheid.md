---
MOC:
tags:
  - note
date: 2026-02-20
about:
  - Dingen om te veranderen voor ESB
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

## Aanpassingen per onderwerp

**LISS variabelen**
- Ook kijken naar vragen over anderen types zwaar werk
- Ook combinatie variabelen maken

**Comparison samples**
- Niet op gender stratisfyen, nadenken over hoe we leeftijd willen stratisfyen
- Weighted draw veranderen naar filteren per jaar oid. Met weighted draw maakt de originele verdeling ook uit. Of de draw kans moet rekening houden met aantal mensen die die groep hebben.
- RVU_like
	- Wat is het doel van deze groep? RVU eligible -> zelfde leeftijd? Ook zelfde gender?
	- Let er op dat eventuele stratification gebeurt na filteren voor employment
- Overwegingen:
	- Welke groepen filteren voor mensen die in de SPOLIS voorkomen?
	- Filteren zodat er geen overlap tussen de samples is? Dat ieder individu in precies eentje zit?

**Checken**
- Checken of de variance van de weighted ding goed wordt berekend.
- Checken of ik de juiste schattingen gebruik voor de juiste groepen (all vs \_like)
- Nadenken of de predictions ook in het verleden mogen liggen: data van latere jaren gebruiken om voorspellingen te make voor eerder

**Extra plotjes**
- Misclassification rates per LISS year
- Als jaren wel beschikbaar zijn, voorspellingen over de jaren vergelijken
- Overwegingen:
	- Characteristics alleen voor LISS 2020 omdat we daar naar kijken?

**Eventueel**
- Overlap tussen LISS en RVU beter gebruiken?
- Meer plotjes maken
	- Met characteristics van wel/geen zwaar werk
	- Prediction performance uitzetten tegen Z
	- Welke features vaker voorkomen met RVU
	- "Waarschijnlijk al eerder" ook uit de SPOLIS filteren en kijken wat voor mensen dit zijn.


## Oude notities
### Oude versie met misschien aanvullingen in Obsidian

FOUTEN:
- ~~RVU\_like sample niet op gender stratifyen. Dan plotje toevoegen van gender distributie~~
- Weighted corrected a voor RVU\_like en unweighted voor random vergelijken met daadwerkelijke (==snap ik niet meer==)
- Checken of de plotjes overeen komen (==snap ik niet meer==)
- Predictions voor 2010 (==snap ik niet meer==)
- Bij random sample comparison, gewoon LISS toevoegen aan de rest. Had makkelijk gekunt en had je geen dubbele gehad. Eventueel nog een losse voor alle leeftijden om te kijken of LISS echt random is. (==snap ik niet meer==)
- ~~Zorgen dat de random en RVU\_like samples gestratified worden op age NADAT ze gefilterd zijn op employed population.~~
- ~~Is die weighted draw nou takke dom? Als er van een bepaalde groep meer voorkomen dan blijft dat? Gewoon aantal filteren per leeftijd.~~
- ~~Bij vergelijken LISS en random, random is gegeven geen RVU-usage. Weer kneiter dom want is dus geen random sample.~~
- LISS weights voor tweede estimate van Se/SP slaan ook nergens op. Zou op groepsniveau moeten gaan, niet op individu niveau, aangezien sommige groepen misschien al oververtegenwoordigd zijn. (==snap ik niet meer==)
- ~~Employed en eligible niet filteren op overlap met exempted? Zorgt ervoor dat vergelijking ten opzichte van gehele populatie is~~
- Voorspelling alleen maken op basis van heden en verleden, niet toekomst (==snap ik niet meer==)
- ~~Plotjes characteristics alleen voor LISS 2020~~


Minder belangrijk:
- More of an exploratory analysis of what features co-appear with RVU (niet belangrijk)
- Mensen met waarschijnlijk al eerder ook uit SPOLIS filteren en meer onderzoek doen. Wanneer kwamen ze voor het laatst voor? Hoe hoog waren de betaalde bedragen? Filteren voor mensen die te oud, te jong zijn.
- ~~Ook mental/manual toevoegen en combinatie van vragen (tenminste 1, allemaal)~~
- ~~LISS niet filteren op domme dingen.~~
- Performance voor verschillende regionen van Z onderzoeken
- ~~Filteren voor geen overlap tussen 2-4 hoeft niet. Misschien zelfs beter niet doen, want dan vergelijk je ten opzichte van de gehele employed/exemption-eligble populatie ipv, de non-users hierbinnen.~~
- ~~Distributies wel/geen zwaar werk uitzetten voor LISS~~
- ~~Overlap van LISS en RVU beter gebruiken~~
- ~~Andere vragen die wel aansluiten bij TNO classificatie~~


Microdata niet nodig:
- Toevoegen relative odds. Waarom odds ratio?
- Plot met hoevaak iedereen LISS heeft ingevuld
- Alpha\_all slaat nergens op
- Contours maken voor relative odds en odds ratio
- Delta method for uncertainty? Lijn voor 95\% confidence toevoegen in plot?



### Future research

Andere vragen:
- Alle van LISS die aansluiten bij TNO definities
- 

Methodologie:
- Groepen beter samplen


### Latere copy uit overleaf met misschien aanvullingen

FOUTEN:
- RVU\_like sample niet op gender stratifyen. Dan plotje toevoegen van gender distributie
- Weighted corrected a voor RVU\_like en unweighted voor random vergelijken met daadwerkelijke
- Checken of de plotjes overeen komen
- Predictions voor 2010
- Bij random sample comparison, gewoon LISS toevoegen aan de rest. Had makkelijk gekunt en had je geen dubbele gehad. Eventueel nog een losse voor alle leeftijden om te kijken of LISS echt random is.
- Zorgen dat de random en RVU\_like samples gestratified worden op age NADAT ze gefilterd zijn op employed population.
- Is die weighted draw nou takke dom? Als er van een bepaalde groep meer voorkomen dan blijft dat? Gewoon aantal filteren per leeftijd.
- Bij vergelijken LISS en random, random is gegeven geen RVU-usage. Weer kneiter dom want is dus geen random sample.
- LISS weights voor tweede estimate van Se/SP slaan ook nergens op. Zou op groepsniveau moeten gaan, niet op individu niveau, aangezien sommige groepen misschien al oververtegenwoordigd zijn.
- Employed en eligible niet filteren op overlap met exempted? Zorgt ervoor dat vergelijking ten opzichte van gehele populatie is
- Variance estimators gaan uit van independence, maar dat is niet zo voor test sample


Minder belangrijk:
- More of an exploratory analysis of what features co-appear with RVU
- Mensen met waarschijnlijk al eerder ook uit SPOLIS filteren en meer onderzoek doen. Wanneer kwamen ze voor het laatst voor? Hoe hoog waren de betaalde bedragen? Filteren voor mensen die te oud, te jong zijn.
- Ook mental/manual toevoegen en combinatie van vragen (tenminste 1, allemaal)
- LISS niet filteren op domme dingen.
- Performance voor verschillende regionen van Z onderzoeken
- Filteren voor geen overlap tussen 2-4 hoeft niet. Misschien zelfs beter niet doen, want dan vergelijk je ten opzichte van de gehele employed/exemption-eligble populatie ipv, de non-users hierbinnen.
- Distributies wel/geen zwaar werk uitzetten voor LISS
- Overlap van LISS en RVU beter gebruiken
- Andere vragen die wel aansluiten bij TNO classificatie
- 35, 15, 50 train val test doen


Microdata niet nodig:
- Toevoegen relative odds. Waarom odds ratio?
- Plot met hoevaak iedereen LISS heeft ingevuld
- Alpha\_all slaat nergens op
- Contours maken voor relative odds en odds ratio
- Delta method for uncertainty? Lijn voor 95\% confidence toevoegen in plot?

