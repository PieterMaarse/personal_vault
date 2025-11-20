---
MOC:
tags:
  - note
date: 2025-11-19
about:
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

Zie [[Data Dismissal Rates Tim]] voor vorige eisen


- Kon geen data vinden over uitgesplitst naar age/education
- Israel mist weer
- Extra landen:
	- Albania
	- Bosnia and Herzegovina
	- Bulgaria
	- Cyprus
	- Iceland
	- Kosovo*
	- Liechtenstein
	- Malta
	- Montenegro
	- North Macedonia
	- Norway
	- Romania
	- Serbia
	- Slovakia
	- Türkiye
	- United Kingdom


Doel:

GDP:
- Per capita
- Jaarlijks
- Uitgesplitst naar education/leeftijd/sector indien beschikbaar
- 2004-2017
- Landen:
	- Austria
	- Belgium
	- Croatia
	- Czech Republic
	- Denmark
	- Estonia
	- Finland
	- France
	- Germany
	- Greece
	- Hungary
	- Ireland
	- Israel
	- Italy
	- Latvia
	- Lithuania
	- Luxembourg
	- Netherlands
	- Poland
	- Portugal
	- Slovenia
	- Spain
	- Sweden
	- Switzerland


## Mogelijke bronnen


Selected datasets:
- Detailed breakdowns of main GDP aggregates (by industry and consumption purpose):
	- [Final consumption expenditure of households, by consumption purpose](https://ec.europa.eu/eurostat/databrowser/view/tec00134/default/table?lang=en&category=t_na10.t_nama10.t_nama_10_dbr)
		- Minder relevant, gaat niet om consumption expenditure


- Basic breakdowns of main GDP aggregates and employment (by industry and by assets):
	- [Employment, domestic concept - Total](https://ec.europa.eu/eurostat/databrowser/view/tec00112/default/table?lang=en&category=t_na10.t_nama10.t_nama_10_bbr)
		- Meer over employment

- Auxiliary indicators (population, GDP per capita and productivity):
	- [Real GDP per capita](https://ec.europa.eu/eurostat/databrowser/view/sdg_08_10/default/table?lang=en&category=t_na10.t_nama10.t_nama_10_aux)
		- Gebaseerd op "GDP and main components per capita"



Detailed datasets:
 - Annual:
	 - [Gross domestic product (GDP) and main components (output, expenditure and income)](https://ec.europa.eu/eurostat/databrowser/view/nama_10_gdp/default/table?lang=en&category=na10.nama10.nama_10_ma)
		 - Niet per capita
	 - [Gross value added and income by main industry (NACE Rev.2 )](https://ec.europa.eu/eurostat/databrowser/view/nama_10_a10/default/table?lang=en&category=na10.nama10.nama_10_ma)
		 - Ook nice
	 - [Gross value added and income by detailed industry (NACE Rev.2 )](https://ec.europa.eu/eurostat/databrowser/view/nama_10_a64/default/table?lang=en&category=na10.nama10.nama_10_ma)
		 - Deze is nice
	 - [Gross domestic product (GDP) and main components per capita](https://ec.europa.eu/eurostat/databrowser/view/nama_10_pc__custom_18969809/default/table)
		 - 

- Quarterly: breakdown by NACE Rev.2 components
- https://ec.europa.eu/eurostat/databrowser/view/namq_10_a10/default/table?lang=en



## Geselecteerde bronnen


 - [Gross value added and income by main industry (NACE Rev.2 )](https://ec.europa.eu/eurostat/databrowser/view/nama_10_a10/default/table?lang=en&category=na10.nama10.nama_10_ma)
	 - Current prices, euro per capita
	 - GDP at market prices

 - [Gross value added and income by detailed industry (NACE Rev.2 )](https://ec.europa.eu/eurostat/databrowser/view/nama_10_a64/default/table?lang=en&category=na10.nama10.nama_10_ma)
	 - Value added, gross
	 - Economic Activities: All NACE activities
	 - Unit of measure: Percentage of total (handig voor naar per capita?)
	 - Alleen Ukraine weggehaald

 - [Gross domestic product (GDP) and main components per capita](https://ec.europa.eu/eurostat/databrowser/view/nama_10_pc__custom_18969809/default/table)
	 - Zonder Ukraine



## Update industries

1. Agriculture, hunting, forestry, fishing 
2. Mining and quarrying 
3. Manufacturing
4. Electricity, gas and water supply
5. Construction 
6. Wholesale and retail trade; repair of m 
7. Hotels and restaurants
8. Transport, storage and communication
9. Financial intermediation 
10. Real estate, renting and business activ 
11. Public administration and defence; comp
12. Education 
13. Health and social work
14. Other community, social and personal se 
   99 99


- A: Hunting niet genoemd
- DE: Water supply niet genoemd, DE samen
- Hotels and restaurants -> Accomodation and food service activities



[A] Agriculture, forestry and fishing Label : Agriculture, forestry and fishing
[B] Code : b . Mining and quarrying Label : Mining and quarrying
[C] Code : c . Manufacturing Label : Manufacturing
[D] Code : d . Electricity, gas, steam and air conditioning supply Label : Electricity, gas, steam and air conditioning supply
[E] Code : e . Water supply; sewerage, waste management and remediation activities Label : Water supply; sewerage, waste management and remediation activities
[F] Code : f . Construction Label : Construction
[G] Code : g . Wholesale and retail trade; repair of motor vehicles and motorcycles Label : Wholesale and retail trade; repair of motor vehicles and motorcycles
[H] Code : h . Transportation and storage Label : Transportation and storage
[I] Code : i . Accommodation and food service activities Label : Accommodation and food service activities
[J] Code : j . Information and communication Label : Information and communication
[K] Code : k . Financial and insurance activities Label : Financial and insurance activities
[L] Code : l . Real estate activities Label : Real estate activities
[M] Code : m . Professional, scientific and technical activities Label : Professional, scientific and technical activities
[N] Code : n . Administrative and support service activities Label : Administrative and support service activities
[O] Code : o . Public administration and defence; compulsory social security Label : Public administration and defence; compulsory social security
[P] Code : p . Education Label : Education
[Q] Code : q . Human health and social work activities Label : Human health and social work activities
[R] Code : r . Arts, entertainment and recreation Label : Arts, entertainment and recreation
[S] Code : s . Other service activities Label : Other service activities
[T] Code : t . Activities of households as employers; undifferentiated goods- and services-producing activities of households for own use Label : Activities of households as employers; undifferentiated goods- and services-producing activities of households for own use
[U] Code : u . Activities of extraterritorial organisations and bodies


| New code | Old number | New industry                                                                                                               | Old industry                            |
| -------- | ---------- | -------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| A        | 1          | Agriculture, forestry and fishing                                                                                          | Agriculture, hunting, forestry, fishing |
| B        | 2          | Mining and quarrying                                                                                                       | Mining and quarrying                    |
| C        | 3          | Manufacturing                                                                                                              | Manufacturing                           |
| D        | 4          | Electricity, gas, steam and air conditioning supply                                                                        | Electricity, gas and water supply       |
| E        | 4          | Water supply; sewerage, waste management and remediation activities                                                        | Electricity, gas and water supply       |
| F        | 5          | Construction                                                                                                               | Construction                            |
| G        | 6          | Wholesale and retail trade; repair of motor vehicles and motorcycles                                                       | Wholesale and retail trade; repair of m |
| H        | 8          | Transportation and storage                                                                                                 | Transport, storage and communication    |
| I        | 7          | Accommodation and food service activities                                                                                  | Hotels and restaurants                  |
| J        | 8          | Information and communication                                                                                              | Transport, storage and communication    |
| K        | 9          | Financial and insurance activities                                                                                         | Financial intermediation                |
| L        | 10         | Real estate activities                                                                                                     | Real estate, renting and business activ |
| M        | 10         | Professional, scientific and technical activities                                                                          | Real estate, renting and business activ |
| N        | 10         | Administrative and support service activities                                                                              | Real estate, renting and business activ |
| O        | 11         | Public administration and defence; compulsory social security                                                              | Public administration and defence; comp |
| P        | 12         | Education                                                                                                                  | Education                               |
| Q        | 13         | Human health and social work activities                                                                                    | Health and social work                  |
| R        | 14         | Arts, entertainment and recreation                                                                                         | Other community, social and personal se |
| S        | 14         | Other service activities                                                                                                   | Other community, social and personal se |
| T        | 14         | Activities of households as employers; undifferentiated goods- and services-producing activities of households for own use | Other community, social and personal se |
| U        | 14         | Activities of extraterritorial organisations and bodies                                                                    | Other community, social and personal se |
Twijfel over: M, T, U


