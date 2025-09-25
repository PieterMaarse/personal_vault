---
MOC:
  - "[[$Scriptie]]"
tags:
  - bron
type: PowerPoint
PDF: "[[PDF_PowerPoint_EBB.pdf]]"
link:
about:
  - Gebruikt machine learning op survey om groepen te classificeren
  - Gemaakt door SEO
gearchiveerd:
by: SEO
relevant_for:
  - ML technieken
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## Notes

- Doen ze feature engineering?

## Summary

Ze willen baankenmerken voorspellen met ML technieken. Hiervoor maken ze gebruik van de Enquête Beroepsbevolking, met 2000 mensen waarvan 1000 zwaar werk hebben.

Ze willen 3 binaire variabelen voorspellen: Thuis werken, Ploegendienst, avond/nachtwerk. Dit doen ze aan de hand van gegevens uit de POLISBUS, GBA en opleidingsgegevens. 

Ze gebruiken 3 modellen (Logit, Gradient Boost, Extreme Gradient Boost), waarbij ze een precision < 90% en recall > 10% willen halen. Extreme Gradient Boost komt het beste uit de test.

CBS veranderd/verbetert vaak de bestanden, dus het is lastig om mensen door de jaren te volgen.


## PDF
![[PDF_PowerPoint_EBB.pdf]]