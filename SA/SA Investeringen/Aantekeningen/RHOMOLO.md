---
MOC:
  - "[[$SA Investeringen]]"
tags:
  - note
  - model
about:
  - SCGE model dat wordt gebruikt voor doorrekeningen investeringen R&D
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## RHOMOLO

RHOMOLO is een Spatial Computable General Equilibrium (SCGE) model dat veel wordt gebruikt om regionaal beleid en de effecten op specifieke sectoren en regio's door te rekenen.

### Hoe werkt het?

#### Overzicht

Het RHOMOLO model modelleert de EU, waarbij de gehele EU wordt opgesplitst in NUTS2 regio's (voor Nederland is dit per provincie) en de rest van de wereld. Elke regio bestaat uit 10 sectoren/industrieën (NACE rev. 2?). Deze regio's worden ruimtelijk gemodelleerd, waardoor een werking tussen sectoren van verschillende regio's (ze handelen met elkaar en er vinden kennis spillovers plaats) kan worden gemodelleerd. 

Een subset van de sectoren is monopolistisch competitief a la Dixit-Stiglitz (?) en de rest is perfect competitief. Bedrijven in elke sector maken gebruik van kapitaal, arbeid, en intermediaire goederen van andere sectoren. 

Elke regio heeft een representatief huishouden dat alle final goods in de economie consumeert. Deze leveren arbeid (laag/middel/hoog) en krijgen salaris, betaling belasting, krijgen geld van de overheid, en krijgen geld uit kapitaal.

RHOMOLO maakt gebruik van ruimtelijke verbindingen tussen regio's, tussen welke handel van goederen en diensten plaats vinden, evenals arbeid en kapitaal. Hierdoor is het mogelijk om beleidsscenario's toe te passen op specifieke regio's en andere voor andere regio's te analyseren wat de effecten zijn.

Investeringen in R&D hebben twee effecten op de economie: 1) productie wordt efficiënter en 2) vraag neemt (tijdelijk) toe (aangezien R&D beleid wordt meegenomen als private investeringen). 

#### Technisch

- Spatial Computable General Equilibrium (SCGE)
- RHOMOLO doet recursief, waarbij elke periode de agents met op dat tijdstip de beste keuzen maken (statisch, kijken niet vooruit)
- In RHOMOLO, elke NUTS2 regio is een eigen economie
- RHOMOLO heeft niet de perfect competition aanname

- Computable: gebruikt data en wordt numeriek opgelost. QUEST niet?
- De grootte van spillovers en hoe snel wordt aangepast aan de kennis hangt af van de elasticiteit (wordt geschat buiten het model?)

- (Sommige?) CGE modellen optimaliseren niet op de lange termijn (one-period), maar het kan ook dynamisch

- Wanneer de parameters zijn gekozen/berekend, kan het gebruikt worden om hypothetische (beleids-)scenario's door te rekenen.

Het berekenen van de gevolgen van R&I beleid bestaat uit drie stappen:
- Kwantificeren van het beleid (bijvoorbeeld meer funding voor R&D modelleren als verminderde risico premie op kapitaal)
- Econometrische schatting van elasticiteiten of het halen uit de literatuur
- Simulatie in RHOMOLO

### Voor- en Nadelen

**Voordelen**
- Veel vormen van beleid kunnen doorgerekend worden
- Het kan specifieke regio's modelleren, waardoor zowel regio-, nationaal- als EU-wijd beleid gemodelleerd kan worden, evenals de effecten op specifiek regio's.
- Het is mogelijk om ruimtelijke concentratie te modelleren (kennis-hubs vs gelijk verspreid over het land)
- Interacties tussen R&I- en cohesiebeleid??
- Kan environmental variabelen meenemen

**Nadelen**
- RHOMOLO is deterministisch en kan alleen point estimates geven van gevolgen van exogene schokken. Risico en onzekerheid kunnen niet worden gemeten.
- Geschatte parameters voor elasticiteit kunnen onbetrouwbaar zijn. Hier worden soms ad hoc sensitiviteitsanalyses voor toegepast.
- R&D wordt niet direct gemeten als losse sector, maar door effecten op hogere productiviteit en vraag.
- RHOMOLO heeft geen endogene financiële fricties
- Data is niet altijd beschikbaar op regionaal niveau. Dit is nodig voor het schatten van endogene groeiparameters.

## Sources

### EC Rapport - RHOMOLO

![[EC Rapport - Moving the Frontier#RHOMOLO]]

