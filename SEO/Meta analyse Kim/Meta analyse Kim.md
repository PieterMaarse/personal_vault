---
MOC:
tags:
  - note
date: 2025-11-07
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
Rayyan account wachtwoord: K1mH3lp3n!

## Stappenplan model

- [ ] API testen
	- [ ] Kun je dingen updaten?
	- [ ] Hoe kun je beslissingen aanpassen?
	- [ ] Kun je een specifiek reden geven: "model"
	- [ ] Kun je notes toevoegen: "gekozen door model"?
- [ ] Refactoren voor mooiere code, niet als script
- [ ] Verifiëren dat test set niet wordt gebruikt voor trainen (essentieel voor goeie inschatting performance!!)
- [ ] Uitbreiden
	- [ ] Keywords includen
	- [ ] Beter features?
	- [ ] Beter embedding model?
	- [ ] Trainen op jargon?
	- [ ] Hyperparameters tunen
- [ ] Checken
	- [ ] Zijn de abstracts niet te lang?
	- [ ] Klopt het dat sommige abstracts "..." bevatten?
	- [ ] Zitten er nog biases in?
- [ ] Verificatie
	- [ ] Stuk of 300 papers met de hand checken of niks gemist
	- [ ] Helemaal random sample


## Oude notes

Checken:
- Aantal labels correct?
- Abstract niet te lang? (meer dan 256 tokens?)
- Trainen op jargon?
- Sommige articles missing abstract en titel?
	- Die komen uit een andere taal
	- Nu vervang ik door NA, maar vervang door eruit te filteren

Optimize weights

Klopt het dat sommige abstracts veel ... bevatten?


