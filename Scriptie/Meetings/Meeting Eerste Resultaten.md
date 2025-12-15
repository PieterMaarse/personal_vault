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
## Aantekeningen


Allereerste resultaat:
- Mensen met supervisory profession lijken ondervertegenwoordigd in RVU gebruik
	- (Nog geen covariates gebruikt


Regressie:
$$ P(RVU) = \beta_0 + \beta_1 \mathbb{1}_{\{\hat{Q}_{prof\ } = 1\}} + \gamma X + \varepsilon$$

Inhoudelijke problemen
- Misclassified binary regressor (invalide inference), zijn manieren voor (onder aannames)
- Hoe vertaalt deze regressie nou echt naar hard werk?
- Data is niet heel betrouwbaar (vindt Magnus belangrijk)



Meer praktische problemen
- Probleem 1?
	- Welke covariates moet ik meenemen?
		- Het voorspelmodel wordt getraind op dezelfde of vergelijkbare features als de regressors in de regressie. Levert dit nog een soort bias op?
		- Voelt een beetje als een soort IV achtig iets?
- Probleem 2?
	- Econometrische analyse: wie meenemen van niet-LISS?
		- In de dataset die ik meeneem voor mijn voorspelling neem ik wel en niet-RVU mee
		- De groep niet RVU is vergelijkbaar in age en gender distributie, maar kan op andere vlakken verschillen
		- Is dat een probleem? Correlatie tussen binary variable en andere covariates?
		- Levert meer vergelijkbare individuen efficientie op?
- Probleem 3?
	- In de dataset waar het voorspelmodel op wordt getraind zijn de observations niet independent
		- Sommige mensen komen veel vaker voor dan anderen (17 vs 1)
		- Elke response heeft nu zelfde weight
		- Wat zijn de effecten daarvan op de betrouwbaarheid van de estimates?
- Vraag:
	- Moet mijn voorspelling wel goed zijn?
	- Hoe selecteer ik de threshold?


## Conclusies

- Belangrijkste toevoeging scriptie: Methode om valide inference te doen met voorspelde survey resultaten
	- Waar moet je rekening mee houden?
	- Wat zijn aannames?
	- Hoe betrouwbaar is inference?
- Belangrijkste eerst doen:
	- Literatuur kijken waar ik rekening mee moet houden (misclassified binary regressor)
		- 
	- In kaart brengen welke dependencies ik heb (correlaties e.d. die kunnen leiden tot invalide inferentie)
		- Theorie:
			- Welke covariates moet ik meenemen?
		- Microdata:
			- Zijn classification errors independent van covariates?
	- Pas later voorspelling weer verbeteren / voor andere variabelen voorspellen



%% - Met misclassified binary regressor, maakt het uit dat we logistic regression doen?
- Vraag: hoe vertaalt de LISS ding naar hard werk?
- Data: hoe betrouwbaar is de data? Hoe kunnen we daar rekening mee houden?
- Wat willen we in de regressie gooien? Wat als covariates? Maakt het uit dat we op vergelijkbare features voorspellen? %%