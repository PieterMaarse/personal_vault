---
MOC:
  - "[[$Scriptie]]"
tags:
  - note
date: 2025-11-10
about:
  - Het voorspelmodel EBB van SEO
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
## Vragen Menno:

- [ ] Welke variabelen werkten goed?
	- [ ] Gewoon alles erin gooien?
		- [ ] Hebben zij wel gedaan voor XGboost, voor logit wel beetje zelf gekeken ook
	- [ ] Features zelf gemaakt?
		- [ ] Een paar
- [ ] Gemaakt in R?
	- [ ] Ja
- [ ] Algemene tips?
	- [ ] Tradeoff tussen precision en recall

## Packages

XGboost:
- tidyverse
- caret
- openxlsx
- xgboost
- MLmetrics
- pROC
- PRROC
- data.table
