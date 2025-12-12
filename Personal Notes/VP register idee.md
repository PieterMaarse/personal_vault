---
MOC:
tags:
  - note
date: 2025-11-20
about:
  - Idee om meldingen van ongepast gedrag bij te houden
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
## Idee

Idee: een register wat anoniem bijhoudt of er al een keer een melding is gemaakt over iemand.

Stappenplan melding:
1. Ontvang melding en handel af
2. Neem de naam van degene door wie ongewenste gedrag is ervaren. Stop in een tool als https://www.simplified.tools/hash_text.
3. Geef de code, je eigen naam en de datum door aan degene die de database beheert.
4. Mocht de persoon er al twee(?) keer in staan, dan krijg je dat te horen, samen met de naam van vorige verwerker(s)

De database heeft dan geen gegevens over wie wat heeft gedaan. De persoon die de database beheert stel geen vragen maar laat alleen weten als de code er al in voor komt.

Database klinkt fancy, maar zal gewoon een excel/spreadsheet zijn. Precieze beleid is eventueel af te stemmen. Wel belangrijk is dat dezelfde naam naar dezelfde code moet leiden. Hiervoor moeten we een vaste manier van namen invoeren afspreken. Aantal keer nadat je te horen krijgt of iemand er al in voor komt kunnen we afstemmen. Eventueel kun je ook nog zeggen of het een "minor" ding of een erger ding is en dan bijvoorbeeld zeggen bij 3 minor dingen of bij 2 major dingen.



- Korte termijn over dezelfde persoon: checken of het niet dezelfde is
- Getallen geheim houden?
	- Deelt de beheerder niet
- Beheerder deelt niks
- Alleen VP en bestuur
- Voorbeeld met foto's in document zetten
- Hash functies checken

Stappenplan:
1. Ik maak draft
2. Tesse kijkt ernaar en vult aan
3. Tesse komt bij me terug met aanpassingen/toevoegingen
4. Tesse overlegt met bestuur/RvC
5. Documenten finalizen
6. Implementeren
7. Belangrijkste meldingen afgelopen tijd erin zetten


## Draft document


### Inleiding

Als iemand ongewenst gedrag vertoont, dan willen we niet dat iedereen hiervan op de hoogte wordt gesteld. We willen zowel de "dader" als het "slachtoffer" privacy gunnen. Vaak zijn er wel mensen die binnen een jaar het meeste meekrijgen, maar tussen jaren gaat deze kennis vaak verloren. Als gevolg hiervan weten we niet of er leden zijn binnen Kraket die herhaaldelijk ongewenst verdrag vertonen.

Om dit probleem te verminderen willen we een anoniem register opstellen dat inzichtelijk maakt of ongewenst gedrag vaker door een persoon is vertoond, terwijl het ook de privacy van alle betrokken en vertrouwelijkheid omtrent meldingen respecteert. Dit document stelt een manier voor waarop dit eventueel zou kunnen.

Doel: Zorgen dat het duidelijk wordt als over dezelfde persoon herhaaldelijk meldingen worden gemaakt, de privacy van alle leden inachtnemend.


### Samenvatting

(misschien terminologie nog even aanpassen)
Melder: Degene die de melding maakt, bv bij het bestuur of een vertrouwenspersoon
Dader: Degene die ongewenst gedrag vertoont
Verwerker: Degene die de melding ontvangt en verwerkt, meestal bestuur of vertrouwenspersoon
Beheerder: Degene die het register beheert

Het idee is heel simpel. Als een verwerker een melding binnenkrijgt, dan geeft deze een code door aan de beheerder. Deze code is een door hash functies geanonimiseerde naam van de dader. Als deze anonieme code nog niet in het register voorkomt, dan is dit de eerste keer dat er iets over deze persoon wordt gemeld en krijgt de verwerker niks te horen. Komt deze anonieme code vaker in het register voor, dan krijgt de verwerker dit te horen, samen met de naam van de persoon die de vorige melding heeft verwerkt. De verwerker van de huidige melding kan dan contact opnemen met de verwerker van de voorgaande melding om samen te kijken of zij het nodig vinden vervolgstappen te ondernemen, zoals naar het bestuur stappen.

Op deze manier wordt geen gevoelige informatie opgeslagen of gedeeld, er wordt immers niet aan de beheerder doorgeven wát er is gebeurd of door wie, maar het wordt wel duidelijk wanneer iemand meerdere keren ongewenst gedrag vertoont.

### Het register

Hieronder een foto van hoe het register eruit zou kunnen zien. Hierin is verwerker degene die de melding doorgeeft, datum spreekt voor zich, en id de geanonimiseerde versie van de naam van de dader.

![[Pasted image 20251211144811.png]]

Dit is alles wat de beheerder te zien krijgt. Zoals je ziet zit er dus heel weinig informatie in. Mocht de beheerder nou een nieuw appje binnenkrijgen met code "133e2...4e7d69b", dan weet de beheerder niet om wie het gaat, maar wel dat deze persoon al twee keer in het register voor komt. De beheerder zal dan tegen degene die hem appt zeggen, "deze persoon komt al voor, ga even met Pieter praten of jullie vervolgstappen nodig vinden".


### Anonieme code

Je eerste vraag is natuurlijk, "maar hoe kom je dan aan die anonieme code". Goeie vraag! Die code is te maken met door de naam van de dader in een hash functie te gooien. Een hash functie, welke je misschien wel hebt gezien in de studie, neemt een woord als input en vertaalt dit naar complete onzin die niet te herleiden is naar de input. Echter, als je dezelfde input er nog eens in gooit dan kom er wel dezelfde output out. Dus, de anonieme code is op geen enkele manier terug te leiden naar de naam van de dader, maar als iemand dezelfde naam erin gooit zal wel dezelfde code eruit komen.

![[Pasted image 20251211145940.png]]

Eén van de mogelijkheden om deze code te maken is via https://www.simplified.tools/hash_text. Hierboven zie je een afbeelding van hoe de website werkt. Bij het vakje "Text" voer je de naam van de dader in en bij het stukje "Digest" komt er een code uit die je kan kopiëren.

Let op: deze functie is hoofdletter-afhankelijk dus het is belangrijk dat DEZELFDE NAAM OP DEZELFDE MANIER WORDT INGEVULD. Ook zijn er bepaalde instellingen die allemaal op dezelfde manier moeten staan om van dezelfde naam dezelfde code te maken.

Mijn voorstel:
- Gebruik SHA-256
- Input:
	- Gebruik bij namen geen hoofdletters, tussenstukken, kommas
	- Gebruik bij meerdere namen alleen de eerste (voor- of achternaam)
	- Bijvoorbeeld:
		- Pieter Maarse -> pieter maarse
		- Floris op 't Root -> floris root
		- Lennard van Duinen Silva Santisteban -> lennard duinen
- Overige instellingen afstemmen, maar dat mogen jullie doen

Eventueel is het ook een goed idee om een standaard algoritme te gebruiken (of te checken of deze link dat is) zodat niet alles verloren gaat wanneer deze website uit de lucht gaat

### Stappenplan verwerker

Wanneer je als vertrouwenspersoon of bestuurslid een melding binnenkrijgt, volg dan de volgende stappen:

1. Ontvang een melding en handel deze af
2. Gooi de naam van de dader door de hash functie en kopieer de code
3. Stuur de code naar de beheerder
4. Krijg je een naam van een voorgaande verwerker terug?
	1. Nee, dan hoef je er niks mee te doen
	2. Ja, neem dan contact op met de vorige verwerker en stem met deze persoon af of vervolgstappen nodig zijn


### Stappenplan beheerder

Wanneer je als beheerder een appje krijgt, volg dan de volgende stappen:

1. Krijg een appje binnen van een verwerker met een code
2. Check met de verwerker of deze de hash functie op de juiste manier heeft gebruikt
3. Schrijf de naam van de verwerker, de datum en de code op in het register
4. Als de code vaker voorkomt in het register, geef dan de naam van de vorige verwerker(s) door
5. Stel geen vragen en deel deze info met niemand

Hierbij is het van belang dat je geen vragen stelt en niet met mensen deelt dat er een melding is binnengekomen.

### Overdragen beheerder

Wanneer een beheerder minder bij Kraket betrokken raakt en zijn functie overgeeft, dan moet alleen het excel bestand worden doorgestuurd en duidelijk zijn voor de nieuwe beheerder wat de procedure is. Er hoeven verder geen inhoudelijke dingen besproken te worden.

Ook zou het een goed idee zijn om alle meldingen ouder dan 5 jaar voor het doorsturen te verwijderen, aangezien deze mensen hoogstwaarschijnlijk geen lid meer zijn van Kraket.



### Opmerkingen

- Technisch gezien is het mogelijk voor de beheerder om namen te proberen om te kijken of codes overeenkomen. Het is de verantwoordelijkheid van de beheerder dit niet te doen en het register vertrouwelijk te behandelen.

- Het register is niet bedoelt om het aantal meldingen binnen Kraket in kaart te brengen. De beheerder zal deze getallen dan ook met niemand delen, ook niet met het bestuur wanneer ze erom vragen.

- Het moet voor vertrouwenspersonen en bestuursleden duidelijk zijn wie de beheerder is. Het is de verantwoordelijkheid van zowel bestuur als terugkerende vertrouwenspersonen dat dit duidelijk wordt doorgegeven.

- Het was nog een idee om eventueel een code mee te geven voor of het een onwenselijk gedrag "heftig" of "onprettig" was. Er zou onderscheid kunnen worden gemaakt met dat er bij een tweede "heftige" melding actie wordt ondernomen, en bij een derde "onprettige". Laten we dit overleggen.