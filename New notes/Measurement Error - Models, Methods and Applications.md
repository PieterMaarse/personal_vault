---
MOC:
tags:
  - bron
type:
PDF: "[[Measurement Error - Models, Methods, and Applications -- John P. Buonaccorsi.pdf]]"
link:
titel:
about:
gearchiveerd:
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## Notes

Prio
- [ ] Introductie om terminologie te snappen
- [ ] Chapter 2 en 3 intro scannen
- [ ] 3.4.1 snappen
- [ ] Chapter 7 erg relevant
	- [ ] 7.4! Ook de papers die hier worden genoemd
- [ ] Chapter 6
	- [ ] Sommige topics lijken relevant



- Lezen:
	- Intro p1
	- Delen Ch3 p33
		- 3.3
		- 3.4.1
		- 3.5.1
	- 7.4 p256
	- 8.6 p309
	- 6.7.7 p182
	- 6.14 p209
	- Validation data: 2-5, 5.7, 6.5
	- 6 wordt aangeraden te lezen


I think we perform pre-stratification as described on p37 (prospective / cohort study)
- We have to assume nondifferential errors, as we do not have a full validation sample, but only for people who we do not know y for. Or can I force it by choosing bound appropriately? By setting true positive equal to true negative?


- Sectie 2 en 3 gaan over pure categorical context, is dat voor mij relevant? Ik heb wel meer data waar ik de predictie op baseer.

### Terminologie

- Misclassification rates vs reclassification rates
- (Non)differential measurement error: W|x,y = W|x
- surrogacy, conditional independence and nondifferential measurement error imply eachother
- Sensitivity: Theta_1|1
- Specificity: Theta_0|0


Snap ik niet:
- Induced model?
- Berkson error
- Replication (in deze context)


## Highlights

> [[Measurement Error - Models, Methods, and Applications -- John P. Buonaccorsi.pdf#page=232&selection=362,0,362,36|p.209:  6.14 Correcting for misclassification]]
> Overzicht wat waar wordt besproken

> [[Measurement Error - Models, Methods, and Applications -- John P. Buonaccorsi.pdf#page=232&selection=367,44,370,72|p.209:  Correcting for misclassification was treated in Chapters 2 and 3 in purely categorical contexts and Section 6.7.7 provided an in depth look at bias induced by misclassification of a predictor in linear regression in the presence of other perfectly measured predictors]]
> Wat is besproken in sectie 2 en 3

> [[Measurement Error - Models, Methods, and Applications -- John P. Buonaccorsi.pdf#page=31&selection=166,0,167,77|p.8:  The three concepts of surrogacy, conditional independence and nondifferential measurement error are equivalent. That is, any one implies the other two]]
> Belangrijk concept

> [[Measurement Error - Models, Methods, and Applications -- John P. Buonaccorsi.pdf#page=167&selection=28,0,29,45|p.144:  The other notable omission in this and subsequent chapters is further discussion of the use of instrumental variables.]]
> Ze bespreken instrumental variables maar kort

> [[Measurement Error - Models, Methods, and Applications -- John P. Buonaccorsi.pdf#page=185&selection=226,0,235,39|p.162:  Nondifferential measurement error in W , with respect to Y , does not imply the misclassification is nondifferential]]
> Nondifferentiality is dus sws niet echt reëel?


## PDF

![[Measurement Error - Models, Methods, and Applications -- John P. Buonaccorsi.pdf]]
%% add "<" na "!" en Alt+r to run %%