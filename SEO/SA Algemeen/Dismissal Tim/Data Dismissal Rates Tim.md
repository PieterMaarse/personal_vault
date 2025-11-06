---
MOC:
  - "[[$SA]]"
tags:
  - note
date: 2025-10-02
about:
  - Vraagje van Tim over dismissal rates in verschillende landen
gearchiveerd:
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## TODO

- [ ] Data zoeken

## Vragen

- [x] Waarom Israel?
- [ ] Unemployment rates?
- [ ] Welke education levels wil je?
- [ ] Jaren komen niet overeen
- [ ] ==Unemployment anders gedefinieerd voor 55-74? opeens heel laag voor 65-74==



## Remarks

- Luxemburg & Israel zitten er niet in
- Bulgaria (BG), Cyprus (CY), Iceland (IS), Malta (MT), Norway (NO), Romania (RO), Slovakia (SK), United Kingdom (UK) wel in deze niet 
- Veel data mist, pas vanaf 2011
- 2021 niet reliable
- Voor leeftijd is gebaseerd op modellen dus afgerond
- Portugal heeft niet naar gender
- Malta heef niet 55+, alleen 15-75
- Heb geschreven op 001800

## Aantekeningen

#### Data eisen

- Dismissal rates & employment rates per jaar (2004-2017)
	- Naar sector, education, gender
	- Liefst alleen 50+ers

#### Eurostat: Labour market flow statistics in the EU

**Linkjes**
- Statistics explained: [link](https://ec.europa.eu/eurostat/statistics-explained/index.php?title=Labour_market_flow_statistics_in_the_EU)
	- [[LMT Statistics Explained]]
	- Detailed information on mean features, legal basis, methodology, data
- Reference metadata: [link](https://ec.europa.eu/eurostat/cache/metadata/en/lfsi_long_esms.htm)
	- Reference metadata describe statistical concepts and methodologies used for the collection and generation of data. They provide information on data quality and assist users in interpreting the data.
	- [[Labour market transitions - LFS longitudinal data (lfsi_long)]]
- Database: [link](https://ec.europa.eu/eurostat/web/lfs/database)

**Data**

Datasets:
- Employment and unemployment -> LFS main indicators -> Labour market transitions -> Twee opties
	- Normale:
		- zonder leeftijd en urbanisation
	- Experimental:
		- ook data op leeftijd (55-75) en urbanisation
		- weinig data dus geschat op basis van modellen

About:
- Laat zien hoe mensen bewegen tussen labour force, unemployment, en out of labour force.

**Remarks**

- Quarterly and yearly unemployed who left the labour force broadly the same?
- From 2021 onwards, labour market flows cover the whole EU;
- the statistics are deemed reliable for policy analysis and other purposes
- Data may differ from national figures due to methodology
- Persons who move nationally, internationally, cannot be contacted, refuse to answer or die are missing from the pseudo-longitudinal sample.
- For the production of flow estimates, the relatively strong assumption has to be made that those who drop out are similar in their labour market transition behaviour to those who stay in the sample

- Only few countries have data before 2011
- Israel is not in the dataset


## Mail Tim

Dit was de vraag van de referee: _Collect and compute **employment rates** and **job loss probabilities** by year and region. Stratify these measures by **education** and **gender** where possible._

Dus ik heb nodig:

- Per land in mijn paper: zie landen in tabel

- Dismissal rates **per jaar (2004-2017)**: kans op ontslag in jaar t = 0

- Naar sector
- Naar education
- Naar gender
- Let op age! het liefst alleen 50 plussers

- Employment rates **per jaar (2004-2017)**: spreekt voor zich

- Naar sector
- Naar education
- Naar gender
- Let op age! het liefst alleen 50 plussers

|            |           |                |             |             |
| ---------- | --------- | -------------- | ----------- | ----------- |
| Austria    | Germany   | Sweden         | Netherlands | Spain       |
| Italy      | France    | Denmark        | Greece      | Switzerland |
| Belgium    | Israel    | Czech Republic | Poland      | Ireland     |
| Luxembourg | Hungary   | Portugal       | Slovenia    | Estonia     |
| Croatia    | Lithuania | Finland        | Latvia      |             |

