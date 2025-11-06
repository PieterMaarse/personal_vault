---
MOC:
  - "[[$SA Investeringen]]"
tags:
  - note
about:
  - Introductie op de onderwijskant van het project
  - Komt uit een mailtje van Hanneke
gearchiveerd: true
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## Note

_Wat zien we nu voor ons (even kort op hoofdlijnen):_

- _­Er bestaat consensus over de positieve uitkomsten van onderwijsuitgaven
- Er is echter nog veel discussie over de heterogeniteit van die effecten per type maatregel (zie het werk van Hanushek)
- Toch zijn er ook nieuwe papers die relatief uniforme uitkomsten van niet-geoormerkte onderwijsinvesteringen vinden op de uitkomstvariabelen toetsuitkomsten en _educational attainment_ (zie het werk van Jackson & Mackevicius). Aanpak is hierbij dat ze meerdere causale studies (met vereiste minstens (quasi)-experimenteel) terugschalen naar een gelijke impuls (+$1000), corrigeren voor variatie, en zo uitkomsten vergelijken. Dan vinden ze dus redelijk uniforme uitkomsten.
- Hanushek en Jackson & Mackevicius samennemend is er dus wel sprake van ==ambivalentie==. Tegelijkertijd is er voor het alternatief, het hanteren van een nul-effect, ook geen wetenschappelijke onderbouwing. Nu stelt het CPB niet dat er een nul-effect is, en geven ze kwalitatieve duiding van de orde van grootte van het effect waar mogelijk, maar toch is dat nul-effect wel hoe het politiek gewaardeerd wordt (mijn lezing).
- Om aan al bovenstaande tegemoet te komen, hebben wij daarom het volgende voor ogen:

- _First-best_ is het toepassen van een causaal micro-rendement op maatregelniveau wanneer evidentie voorhanden is. Hierbij berusten we ons in eerste instantie op ==de Kansrijk serie==, maar dit kan natuurlijk aangevuld worden met nieuwe studies. Gezien de heterogeniteit van de effecten van maatregelen heeft deze methode de voorkeur.
- Dan rest wat te doen met de _blinde vlekken_. Dit is het grotere probleem: voor veel maatregelen is geen ==micro-evidentie==. In plaats van een ==nul-effect== op deze blinde vlekken, zien wij voor ons om op een deel van deze blinde vlekken een categorisch rendement toe te passen, zoals in Jackson & Mackevicius. Dit zou dan alleen kunnen voor niet-geoormerkte uitgaven aan het onderwijs (via ==lump-sum== of niet-geoormerkte subsidies). Ze vinden echter wel een verschillend effect voor hoge versus lage SES kinderen: het effect is sterker wanneer de kinderen uit een gezin met een lager inkomen komen. Dat (en andere studies die dit ook onderschrijven) is aanleiding om het categorisch rendement nog wel uit te splitsen naar doelgroep hoge of lage SES. Dit categorische rendement wordt op eenzelfde manier als bij Kansrijk vertaald naar de Nederlandse context: omdat het een studie uit de VS betreft, zijn de te verwachten effecten in NL kleiner.
- Voor specifiekere maatregelen waar géén evidentie voor is, zijn we er nog niet over uit wat verstandig is. Een ‘nul’-effect lijkt onrealistisch en staat experimenteel/nieuw beleid in de weg. Tegelijkertijd moet je een eventueel rendement wel empirisch kunnen onderbouwen.

- De modelmatige doorrekening zijn we nog niet helemaal over uit. Op hoofdlijnen zijn er twee opties: (1) een partieel model, en (2) een model dat rekening houdt met algemene evenwichten (inc. feedbackloops). Een model dat op de tweede manier is ingestoken kennen wij eigenlijk niet, en lijkt ons onhaalbaar. Het zal dus een variant van (1) moeten worden, een partieel model. Hierin zijn echter ook nog keuzes te maken over het detailniveau, wat wij verder moeten uitdenken. In de basis zal dit de methode van Kansrijk volgen, waarbij doorrekening gebaseerd is op het Human Capital model. Waar Kansrijk het niet doorvertaalt naar een bbp-effect, willen wij dit wel gaan doen. De Kansrijk-methode zien wij eigenlijk als de meest ‘simpele’ variant, deze zou je eventueel ook nog kunnen uitbreiden met meerdere indicatoren en intermediairs, waardoor je de mechanismen en verdelingseffecten in beeld kan brengen (zie Bussink & ter Weel voor inspiratie). Dit maakt de exercitie tegelijkertijd ook weer complexer.

_Wat willen we graag bespreken:_

- Het categorische rendement: hoe kijk jij aan tegen de aanpak om een categorisch rendement toe te passen op niet-geoormerkte verhoging van het budget van scholen, gebaseerd op Jackson & Mackevicius? Hierbij wat subvragen:

- Deze studie richt zich op K12-education: dat is van _kindergarten_ (leeftijd 5/6) tot _12th grade_ (leeftijd 17/18). Wij zouden die rendementen dan dus op het ==FO== kunnen toepassen.  Het gaat om algemene verhogingen van het schoolbudget, dus het is niet op te splitsen naar lagere niveaus. Voor het mbo en ho hebben we nog geen vergelijkbare papers gevonden. Ken jij papers die dit doen voor die groepen? Of meerdere papers voor po/vo. Hoeft uiteraard niet uit de VS te zijn.
- Het paper van Jackson & Mackevicius vindt geen bewijs voor afnemende meeropbrengsten. Dit doen ze door te kijken naar de impact van $1000 extra bij verschillende baseline niveaus van school budgets. Ze stellen zelf dat dit niet zo gek is, aangezien scholen het geld vrij mogen besteden en het dus automatisch alloceren naar waar de meest optimale/grote uitkomsten liggen. ==Dat veronderstelt dat scholen momenteel nog ver genoeg verwijderd zijn van het optimale budget dat een optimale besteding _voorlopig_ nog uit kan. Hoe kijk jij hiernaar?==

- In het verlengde van bovenstaande: we proberen nog uit te zoeken hoe om te gaan met afwijkingen van de impuls. Zowel in bedragen als in duur. Jackon & Mackevicius hanteren hier ook een methode voor. In hun aanpak rekenen ze alles namelijk om naar een gelijke periode (impuls gedurende 4 jaar) en een gelijk bedrag ($1000 per jaar).

- _Voor de tijdsduur_: als ze een effect vinden gemeten over twee jaar, vermenigvuldigen ze dit met twee om het vierjaarlijkse effect te krijgen. Hierbij hanteren ze dus constante returns over meerdere jaren. Dit onderbouwen ze met empirisch bewijs dat de voordelen van toegenomen spending ongeveer lineair toenemen door verschillende uitkomsten tegen verschillende duur van de interventie te plotten (zie figuur A.12 van de bijlage). 
- _Voor de kosten:_ hierbij rekenen ze eerst terug naar de kosten van een basisjaar om te corrigeren voor inflatie. Aangezien ze alles uitdrukken in termen van vier jaar, berekenen ze per maatregel de gemiddelde uitgaven per jaar gedurende de vier jaar voordat er effect wordt gezien (dus voordat de toetsscore toeneemt). Voor een permanente toename in kosten, is het totale four-year verschil in spending dus 4x deze jaarlijkse toename. Wanneer er een ingroeipad is gebruikt, gebruiken ze de gemiddelde kosten per jaar. Dit schalen ze dan tot het om een bedrag van $1000 per jaar gaat. Ook hierbij hanteren ze constante kosten. Ze houden uiteraard wel rekening met effecten in logaritmische vorm.
- Een heel simpel voorbeeld: een studie vindt een effect van 0,12 SD na 7 jaar als er gedurende 7 jaar $600 per leerling wordt uitgegeven. Het effect na 4 jaar bij een uitgave van $1000 gedurende 4 jaar is dan: 0,12*(4/7)*(1000/600)
- Dit soort aannames zijn enorm handig bij een doorrekening, maar voelen ook wat kort door de bocht. Hoe reflecteer jij hierop, en weet jij of ander onderzoek dit tegenspreekt?

- Tot slot: de studies schatten effecten in leerwinst vaak op de relatief korte termijn. Ook in de Kansrijk-serie van het CPB wordt hiermee doorgerekend alsof dit effect in leerwinst permanent is. Er wordt geschat op basis van CITO-scores wat het rendement is van een SD-leerwinst, en de hoeveelheid SD-leerwinst die een maatregel oplevert wordt zo vertaald naar extra inkomen over de levensloop. Bijvoorbeeld de studie van de Booij e.a. (2015) schat het effect van homogene klassen met een experiment in het eerste jaar van de bacheloropleiding. Hierbij vindt hij een effect van 0,18SD leerwinst aan het einde van het jaar. Het CPB rekent door met deze leerwinst. Ze schrijven hier niet op af. Verhogingen hebben een permanent karakter. Dit is in zekere zin te verwantwoorden, doordat ze de returns in cito-scores ook schatten op gerealiseeerd inkomen (waar dus veroudering al in zou moeten zitten). Maar in die schatting van inkomenseffecten op CITO-scores speelt de ability bias wel mee lijkt mij (ze geven ook aan dat het puur correlatie is). Daarmee overschat je dan misschien de inkomenswinst per SD leerwinst, en onderschat je de afschrijving (er even vanuit gaande de dat basis ability minder hard afschrijft dan andere aangeleerde vaardigheden – maar ik weet eigenlijk niet of dat strookt met de literatuur). Hoe reflecteer jij op deze onderwijsuitkomsten/rendementen op de lange termijn?
- ==Mijn idee hierover: Heb het niet goed gelezen, maar iets wat bij mij een beetje knaagt is wat je eerder zei over dat de effecten op kinderen met lage SAS groter zijn. In hoeverre wordt salaris verklaard door cito score en in hoeverre door de SAS? En wat is de werking van SAS op cito score? Als kinderen met hogere SAS zowel hogere cito scores als hogere salarissen hebben, dan moet je oppassen dat je het effect wat eigenlijk vanuit de SAS komt niet ten onrechte toekent aan de cito score.==

- Bovendien: stel je zou dit doorrekenen op basis van Jackson & Mackevicius. Dan zou je zeggen dat je als je in jaar 2 van de bachelor weer ==homogene klasse==n hanteert, je weer 0,18 SD leerwinst krijgt, en het jaar daarna ook. Met andere woorden: als we de gehele bachelor in homogene klassen opdelen, heb je 3x0,18 = 0,54 SD leerwinst. Lijkt jou dat realistisch?

_Referenties:_

- Booij, A.S., E. Leuven en H. Oosterbeek, 2015, Ability Peer Effects in University: Evidence from a Randomized Experiment, IZA Discussion Paper 8769.
- [Bussink & Ter Weel](https://eur05.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.iza.org%2Fpublications%2Fdp%2F15649%2Fcosts-and-benefits-of-an-individual-learning-account-ila-a-simulation-analysis-for-the-netherlands&data=05%7C02%7Cp.maarse%40seo.nl%7C6646bc22aa4f44156d0d08ddebb8695d%7Cb926ce648aac4a3ea80155ad78311c67%7C0%7C0%7C638925899455610083%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=6nE%2Fcbqdln1mb4DGPs1X%2BLai99muLhChs6RYuyR9KvM%3D&reserved=0 "Original URL: https://www.iza.org/publications/dp/15649/costs-and-benefits-of-an-individual-learning-account-ila-a-simulation-analysis-for-the-netherlands. Click or tap if you trust this link.")
- Hanushek, E. A. (2015). Does Money Matter after All? Stanford University. Geraadpleegd op 29 augustus 2025, van [https://hanushek.stanford.edu/opinions/does-money-matter-after-all](https://eur05.safelinks.protection.outlook.com/?url=https%3A%2F%2Fhanushek.stanford.edu%2Fopinions%2Fdoes-money-matter-after-all&data=05%7C02%7Cp.maarse%40seo.nl%7C6646bc22aa4f44156d0d08ddebb8695d%7Cb926ce648aac4a3ea80155ad78311c67%7C0%7C0%7C638925899455630163%7CUnknown%7CTWFpbGZsb3d8eyJFbXB0eU1hcGkiOnRydWUsIlYiOiIwLjAuMDAwMCIsIlAiOiJXaW4zMiIsIkFOIjoiTWFpbCIsIldUIjoyfQ%3D%3D%7C0%7C%7C%7C&sdata=mzqk9k74nk549JlCB3%2Fb8xL%2Fx6qGWInXlggAUPma9wQ%3D&reserved=0 "Original URL: https://hanushek.stanford.edu/opinions/does-money-matter-after-all. Click or tap if you trust this link.")
- Hanushek, E. A. (1979). The economics of schooling: Production and efficiency in public schools. _Journal of Economic Literature, 17_(3), 1141–1177.
- Hanushek, E. A., & Woessmann, L. (2012). The economic benefit of educational reform in the European Union. CESifo Economic Studies, 58(1), 73–109.
- Jackson, C. K., & Mackevicius, C. L. (2024). What impacts can we expect from school spending policy? Evidence from evaluations in the United States. _American Economic Journal: Applied Economics, 16_(1), 412–446.