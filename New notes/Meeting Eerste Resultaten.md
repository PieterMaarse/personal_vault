---
MOC:
  - "[[$Scriptie]]"
tags:
  - meeting
meeting_with:
  - Jellien Knol
date: 2025-12-15
discussed:
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## Te bespreken

- [ ] 

## Aantekeningen

- Misclassified binary regressor
- Econometrische analyse: wie meenemen van niet-LISS?
- Probleem 1?
	- In de dataset waar het model op wordt getraind zijn de observations niet independent
	- Sommige mensen komen veel vaker voor dan anderen (17 vs 1)
	- Wat zijn de effecten daarvan op de betrouwbaarheid van de estimates?
- Probleem 2?
	- Het voorspelmodel wordt getraind op dezelfde of vergelijkbare features als de regressors in de regressie. Levert dit nog een soort bias op?
- Probleem 3?
	- In de dataset die ik meeneem voor mijn voorspelling neem ik wel en niet-RVU mee
	- De groep niet RVU is vergelijkbaar in age en gender distributie, maar kan op andere vlakken verschillen
	- Is dat een probleem? Correlatie tussen binary variable en andere covariates?
- Vraag:
	- Moet mijn voorspelling wel goed zijn? Of hebben we liever een minder zwarte doos?


- Met misclassified binary regressor, maakt het uit dat we logistic regression doen?