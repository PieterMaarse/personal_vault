---
MOC:
  - "[[$Scriptie]]"
  - "[[$Data Aantekeningen]]"
tags:
  - note
  - data
about:
  - Polis administratie?
data_source: Microdata
nrows: 63372046
ncols: 133
documentation: "[[spolisbus.pdf]]"
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

- [ ] Geconverteerde bestanden map die jullie gebruiken bestaat niet?
- [ ] Mensen hebben negatief basisloon?
- [ ] Zijn RVUs te herkennen aan dat ze geen heffing hoeven te betalen? Zo onderscheid maken?
- [ ] Er zijn mensen voor wie van de ene op de andere maand wel de SBEID verandert, maar niet de IKVID
- [ ] 2020-11 en 2021-01, mensen met meerdere contracten dan eentje minder, daarna eentje meer?
- [ ] Er zijn mensen met basisuren 400?

## Aantekeningen

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

- Mensen in de sector 03 (bouw?) hebben vaker dubbele contracten! Eventuele voorspellende feature

- Zowel lonen als uitkeringen en pensioenen
- Het bestand wordt gecontroleerd op SBI-sectie-niveau. Bij gedetailleerder niveau dient de gebruiker zelf de plausibiliteit per sbi-niveau te controleren.
- ==Bij het maken van de grote dataset van SPOLIS voor mensen in RVU, LISS, RVU_like en 100k random gaf hij een runtime error, maar het lijkt het wel gewoon goed te hebben gedaan. De dataset was opgeslagen aan het einde en lijkt compleet. Het aantal distinct RINPERSOON klopt==
	- Ongeveer 2000 mensen zitten er dubbel in


### Koppeling met RVU

- Percentage mensen dat in 2021 RVU had neemt toe naarmate SPOLIS later genomen is
	- Gek want je zou verwachten dat mensen die eerder met RVU gaan hier ook eerder uit verdwijnen
- Mensen die in 2023 RVU troffen komen naar verhouding veel minder voor in latere SPOLIS, vergeleken met 2021 RVU.
	- SPOLIS 2021 -> 2025 :
		- RVU 21 -> /2
		- RVU 23 -> /12
- Voor 2021 is Eerder waarschijnlijk al RVU zwaar oververtegenwoordigd in 2025
	- Mensen die waarschijnlijk eerder RVU hebben getroffen blijven langer in SPOLIS data
- RVU in 2022: SPOLIS 2023 -> 2025: Aantal mensen neem toe?
- SPOLIS 2021: Eerder waarschijnlijk RVU ondervertegenwoordigd?


Eerder RVU eruit gooien

Ik denk dat er een fout zit in de Eerder waarschijnlijk al RVU?

### Datasets properties

Vlm staat het geordend op rinpersoons... niet random.

2025:
- De eerste 5001 variabalen hebben RINPERSOONS = A. 
- n_distinct: 
- Percentages:
	- 7M: 52.44966%


2023: 
- 126,420,158 rijen
- 10,783 RINPERSOONS A, 126,408,260 R, 1115 S
- SSRTIV: 11: 6,363,629, 13: 63,806, 15:116,210,855, 17: 3,781,868
- n_distinct(RINPERSOON) - 9,740,476 (13pp)
	- Percentages: 
		- 7M: 49.85716%

polis_23_7M heeft random sample met helft van de mensen


2021:
- rijen 119,168,165
- n_distinct(RINPERSOON) - 9,328,255
- perc 7M: 51.42622%

### Laad tijden

Bij 2025 (63,372,046 rijen, tot (en met?) juni)
- 8 variabelen en alle rijen: 734 seconden
- 4 variabelen en alle rijen: 500 seconden
- 1 variabele en alle rijen: 350 seconden
Dus, bij benadering lineair / net toenemend stijgend naar variabelen?


### Relevante variabelen

Zie documentatie voor alle variabelen

Toevoegen:
- [ ] Iets van datum?
- [ ] Verder kijken vanaf SBASISUREN

Relevant:

| Variabele           | Definitie                                                                                                                                                      | Comment |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| RINPERSOON          |                                                                                                                                                                |         |
| RINPERSOONS         |                                                                                                                                                                |         |
| IKVID               | Dit nummer identificeert een inkomstenverhouding volgens het Uitvoeringsinstituut Werknemersverzekeringen (UWV). Het is een betekenis- en dimensieloos nummer. |         |
| SDATUMAANVANGIKO    | De datum van aanvang van een inkomstenopgave of de aanvang van een verslagperiode.                                                                             |         |
| SDATUMEINDEIKO      | De datum einde van een inkomstenopgave of einde van een verslagperiode van een<br>inkomstenverhouding.                                                         |         |
| SAUTOZAAK           | De waarde van een bijtelling bij een loon voor het privégebruik auto van de zaak.                                                                              |         |
| SBASISLOON          | Bedrag aan basisloon: loon exclusief bijzondere beloningen, toeslagen en overwerkloon                                                                          |         |
| SBIJZONDEREBELONING | De waarde van de niet regelmatig betaalde beloningen, die tot het brutoloon behoren.                                                                           |         |
| SSOORTBAAN          | Het soort beroep of functie dat wordt uitgeoefend door een persoon.                                                                                            |         |
| SBEID               | Het identificerende nummer van een feitelijke actor in het productieproces die gekenmerkt<br>wordt door autonomie, beschrijfbaarheid en externe gerichtheid.   |         |
| SSECT               | De sector waar een inkomstenverhouding onder valt.                                                                                                             |         |


Eventueel relevant:

| Variabele      | Definitie                                                                                                                                                                                                  |                                            |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| SBASISUREN     | Het aantal verloonde uren van een inkomstenverhouding minus de overwerkuren.                                                                                                                               |                                            |
| SSRTIV         | Het soort inkomstenverhouding van een persoon                                                                                                                                                              |                                            |
| SVOLTIJDDAGEN  | Het aantal voltijddagen van een inkomstenverhouding                                                                                                                                                        |                                            |
| SWRDLN         | De waarde van het loon dat niet in geld is uitgekeerd en waarop loonbelasting/premie volksverzekeringen moet worden ingehouden en waarover premies voor de werknemersverzekeringen moet worden afgedragen. |                                            |
| SCAO_crypt     | De collectieve arbeidsovereenkomst (cao) of arbeidsvoorwaardenregeling die op de inkomstenverhouding van toepassing is                                                                                     |                                            |
| SCDAARD        | Soort arbeidsverhouding bepalend voor de vaststelling dat een werknemer verplicht verzekerd<br>is voor de werknemersverzekeringen.                                                                         | Heeft aparte maatstaf voor ambtenaar! (13) |
| SCDRDNGNBIJT   | De reden waarom er geen bijtelling voor het privégebruik van een ter beschikking gestelde<br>auto is.                                                                                                      |                                            |
| SCAOSECTOR     | Een Collectieve ArbeidsOvereenkomst (CAO)-sector van een bedrijf of instelling.                                                                                                                            |                                            |
| SSOORTBAAN     | Het soort beroep of functie dat wordt uitgeoefend door een persoon.                                                                                                                                        | Check of deze voor onze jaren is           |
| CdRdnEindArbov | De reden voor het eindigen van een arbeidsverhouding.                                                                                                                                                      | Eventueel om RVUs te filteren?             |
| CdCaoInl_crypt | De collectieve arbeidsovereenkomst (cao) of arbeidsvoorwaardenregeling die op de inlener<br>van toepassing is.                                                                                             |                                            |


Toch niet relevant


| Variabele     | Definitie                                                                                                                                                                                                  | Comment                                    |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| SEXTRSAL      | Bedrag dat is uitbetaald als extra periode salaris                                                                                                                                                         | Veel 0                                     |
| SINCIDENTSAL  | Bedrag dat in het loontijdvak is uitbetaald als incidenteel salaris                                                                                                                                        | Vaak zelfde als Bijzondere                 |

