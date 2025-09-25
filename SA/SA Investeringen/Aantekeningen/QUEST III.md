---
MOC:
  - "[[$SA Investeringen]]"
tags:
  - note
  - model
about:
  - DSGE model dat wordt gebruikt voor doorrekeningen investeringen R&D
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## QUEST III

QUEST III is het model dat wordt gebuikt om EU wijde beleidsmaatregelen door te rekenen. Het is een New-Keynsian Dynamic Stochastic General Equilibrium (DSGE). Omdat de creatie en adoptie van kennis apart gemodelleerd worden kan het goed gebruikt worden om R&I beleid te evalueren.

Hoewel het in de praktijk veel wordt gebruikt, o.a. om de de investeringen van de Horizon Europe en Next Generation EU programma's door te rekenen, beargumenteer het CPB in hun rapport dat het gebruik om Nederlandse investeringen in R&D door te rekenen geen betrouwbare resultaten op zou leveren.


### **Vragen**
Hoe modelleren ze extra investeringen? hoe is dat differentieerbaar in het model? welke aannames maken ze? hoe gaan ze om met de onzekerheid?

### Hoe werkt het?

#### Overzicht

QUEST III modelleert huishoudens, producenten van eindproducten, producenten van intermediaire goederen, een onderzoekssector, een overheid, en een centrale bank. Dit model maakt geen onderscheid tussen verschillende industrieën/sectoren of regio's binnen Nederland.

De onderzoekssector bestaat uit onderzoeksinstituten en technologie adopters. Ideeën worden gemaakt in de eerste en deze worden vertaald naar technologie in de tweede. Wanneer deze ideeën vertaald zijn naar technologie zorgen ze ervoor dat intermediaire goederen beter (efficiënter? wordt niet duidelijk uitgelegd) kunnen worden geproduceerd.

In dit process hangt de productie van ideeën af van het aantal high-skilled onderzoekers in de R&D sector, en niet alleen van het kennis niveau van het eigen land, maar ook van andere landen. De grootte van deze kennis-spillovers zijn afhankelijk van de hoeveelheid handel die wordt gedreven met specifieke landen en worden via het adoptie-proces vertaald naar betere technologieën.

Verder doen ze nog een aantal aannames, waarvan sommige negatieve en sommige positieve effecten hebben.
- Homogene bedrijven, wat betekent dat ze allemaal even efficiënt zijn. Dit impliceert dat ze ook allemaal hetzelfde reageren op technologieveranderingen, wat in de praktijk niet waar is.
- Wel heterogene arbeiders, waardoor 1) de effecten op de inkomensdistributie kunnen worden doorgerekend en 2) er rekening mee wordt gehouden dat skilled labour schaar is
- Twee typen huishoudens: met en zonder beperkte liquiditeit
- Geadopteerde technologieën zijn, door middel van patenten, eigendom van huishoudens met liquiditeit. Wanneer deze technologieën worden gebruikt in productie krijgen deze huishoudens hier geld voor.
- De centrale bank zet de rentevoet door middel van een "Taylor type" regel

Hoewel de er geen publieke R&D is en de publieke sector niet direct bijdraagt aan de diffusie van kennis kan dit wel op een aantal manieren worden gestuurd.
- **Subsidies** kunnen worden gemodelleerd door de salarissen van onderzoekers (deels) te betalen
- **Publieke inkopen** kunnen worden gemodelleerd door het publiek kapitaal te vergroten, wat de productiviteit van bedrijven verbeterd, waardoor er meer vraag is naar intermediaire goederen, en dus ook naar R&D.
- De overheid kan **belastingen op technologie** verlagen, waardoor het goedkoper wordt om technologieën te gebruiken, wat de vraag vergroot
- **Publieke leningen en VC** kunnen worden gestimuleerd door de risicovoet van activa te verlagen
- **Administratieve lasten** kunnen worden verlicht door het makkelijker te maken voor bedrijven om te starten met produceren
- **Belastingen** op consumptie, arbeid en inkomen uit kapitaal kunnen worden veranderd
- **Wetgeving over competiti**e kan worden gesimuleerd door de winstmarges aan te passen
- **Sector-specifiek beleid** kan worden doorgerekend door specifiek sectoren zwaarder te laten wegen
- **Monetair en fiscaal beleid** kunnen worden onderzocht door te kijken naar gesimuleerde uitgaven en publieke schulden

Om beleid door te rekenen, moet een specifiek voorstel meestal dus eerst omgerekend worden naar termijn die in het model kunnen worden meegenomen. Ik denk (moet ik checken) dat bijvoorbeeld uitgaven vanuit de publieke sector leiden tot extra uitgaven van de private sector (bijvoorbeeld op basis van de studie van TNO), waardoor de input in het model de vergrote vraag is, die volgt van de verwachte totale extra uitgaven.

Parameters in dit model, zoals de elasticiteit van hoe erg het binnenlandse kennis-niveau afhangt van het buitenlandse of hoe snel technologie verouderd, moeten worden gekalibreerd. Dit betekent dat het niet door het model zelf wordt geschat, maar van tevoren moet worden meegeven, gebaseerd op een goede schatting. De parameters van het model worden dus niet direct "getraind" op data. Echter zijn deze schatting vaak wel gebaseerd op eerdere econometrische schattingen, maar dit kan ook op basis van literatuur.

Het CPB haalt de volgende punten van kritiek aan:
1. Bedrijven zijn homogeen
2. Financiële fricties kunnen niet worden meegenomen
3. Er wordt geen onderscheid gemaakt tussen private en publieke R&D
4. Cruciale parameters zijn niet betrouwbaar gekalibreerd (/geschat) en niet genoeg gebaseerd op recente data
5. Technologische ontwikkeling gebeurt mondiaal en interacties tussen nationaal en mondiaal wordt niet goed meegenomen
6. Doorbraaktechnologieën worden niet meegenomen, terwijl deze de grootste productiviteitsgroei als gevolg hebben
7. De richting/aard van innovatie wordt niet meegenomen. Innovatie die leidt tot meer uitstoot wordt gelijk gesteld aan groene innovatie

Als reactie daarop valt het volgende te zeggen:
1. Er zijn papers die dit meenemen, maar ik weet niet zeker of dit ook goed is gedaan voor DSGE
2. De commissie zegt dat exogene risicopremies op niet-tastbaar kapitaal eventueel financiële fricties kunnen weerspiegelen. Ook is de paper van Benedetti-Fasil et al. (2020) hiermee aan de slag gegaan.
3. De commissie zegt dat een extensie hiervoor gebaseerd kan worden op Akcigit et al. (2020)
4. Dat zal je altijd hebben. All models are wrong, but some are useful. Voor hun voorbeeld waarom het niet kan zeggen ze dat een schatting van de Amerikaanse economie in 2020 een andere waarde geeft dan die van het huidige QUEST model uit 2007. betekent dit dat het niet betrouwbaar kan voor Nederland?
5. Er is wel een "rest van de wereld" in QUEST, ik geloof dat deze ook effect heeft op de innovatie tak, maar dat zou ik voor de zekerheid moeten uitzoeken. Het model is inderdaad wel gedetailleerder voor de EU, maar of dit een probleem is kan ter discussie worden gesteld.
6. Met doorbraakeffecten bedoelen ze uitvindingen als de stoommachines of het internet. Dit heeft inderdaad de grootste effecten, maar hoe belangrijk is het om dit expliciet mee te nemen in het model? Een model probeert nooit de exacte waarheid te voorspellen. Waarom zou je niet iets als de verwachte waarde kunnen meenemen?
7. Hoewel dit een relevant onderwerp is, is dat het ook voor ons doel? Houdt de doorrekening rekening met het effect op het klimaat?

Daarnaast stelt de commissie dat R&I een belangrijke driver is van middel- en langetermijngroei. Een goed macromodel zou een passende modellering van R&I mee moeten nemen. Ze leggen er de nadruk op dat "all models are wrong, but some are useful". Bij elke doorrekening moet er gekozen worden tussen welke aspecten belangrijk zijn om het beoogde doel goed te modelleren. Hiervoor zal gekozen moeten worden wat wel en niet relevant is om mee te nemen. 

Samengevat, een deel van de kritiek van het CPB is terecht. Echter stelt de Europese Commissie dat R&I belangrijk is om mee te nemen in modellen, en zijn er een aantal recente beschikbare submodules die een deel van deze problemen proberen op te lossen.



%% Productiegroei wordt gemodelleerd door technologieontwikkelingen te veronderstellen als (semi-)endogeen, waarbij dus onderscheid wordt gemaakt tussen het ontstaan van kennis, en de adoptie van kennis in productie. Om technologie-ontwikkelingen specifiek te kunnen modelleren wordt productie opgesplitst in 3 delen:
- Research institutes: verzinnen nieuwe technologieën
	- Hangt af van kennis, in zowel binnen als buitenland, en hoeveelheid high skilled labour. 
	- Hoe zwaar elk ander land meeweegt hangt af van hoeveel handel er gedreven wordt.
	- Dit gebeurt semi-endogeen.
- Technology adopters: vertalen deze ideeën naar betere intermediate goods
	- Hangt af van hoeveelheid high skilled labour, kapitaal, ==licensed technologies?==
- Production: produceren horizontaal gedifferentieerde producten
	- Hangt af van intermediate goods en arbeid van de drie kennis niveaus

Daarnaast zijn er huishoudens twee type huishoudens:
- Niet-liquideitsbeperkt: Hebben toegang tot financiële markten en kunnen investeren in patenten, die ze licenseren aan intermediaire goederen producenten.
- Liquiditeitsbeperkt: Hebben deze toegang niet

Tenslotte zijn er de:
- De overheid: heft belastingen en betaalt subsidies
- Centrale bank: bepaald de rentevoet

The QUEST III model distinguishes between _basic research_ (creation of new ideas, raising scientific knowledge) and _applied research_ (adoption of ideas into production).

Is technology adaption sector nou iets anders dan de intermediary goods? %%

#### Technisch

Zet een aantal equilibrium equations, voor household spending, government spending en business spending. Hier komt een "stead-state", vanwaar je impulse responses kan doen. Er wordt rekening gehouden met stochastische input.

Elasticities are taken from the literature?


### Voor- en nadelen

**Voordelen**

Het model heeft een gedefinieerde welfare function. De effecten, zowel de kosten als baten, van verschillende beleidsmaatregelen op de economie kunnen worden doorgerekend, van belasting tot onderwijs. Dit model kan dan ook gebruikt worden om potentiële effecten op BBP te berekenen van verschillende beleidswijzigingen.

QUEST kan een aantal relevante features en enablers van creatie en diffusie van technologie meenemen:
- Niet-rivaliteit
- Patenten
- Arbeidsniveaus
- Handel en kennisspillovers
- Onderscheid tussen nationaal en supranationaal beleid
- 

Daarnaast kan het de creatie van kennis en de adoptie ervan los modelleren en is het mogelijk te modelleren door welke kanalen de effecten van beleid door de economie bewegen.

**Nadelen**

Ook zijn er een aantal nadelen:
- Geen heterogeniteit in bedrijven
	- Geen financiële fricties, waar sommige bedrijven meer last van hebben dan andere
- Geen verschil in publieke en private investeringen. Alleen de private sector wordt meegenomen.
- Menselijk kapitaal groeit niet endogeen, waardoor de effecten van educatie op innovatie niet worden meegenomen
- Geen environmental component
- Geen randomness in de uitkomsten van R&D



## Sources

Aantekeningen EC rapport en CPB Rapport

### EC Rapport - QUEST III

![[EC Rapport - Moving the Frontier#QUEST III]]


### CPB Rapport

![[CPB Rapport - QUEST III#Aantekeningen]]