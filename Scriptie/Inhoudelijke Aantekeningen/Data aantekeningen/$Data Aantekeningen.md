---
MOC:
  - "[[$Scriptie]]"
tags:
  - note
date: 2025-10-07
about:
  - Overzicht en vragen omtrent de gebruikte LISS en microdata data
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

- [[Microdata bestanden met toegang]]

## Overzicht
```dataview
TABLE data_source, about
WHERE contains(MOC, this.file.link)
```

## Vragen

### BETAB

![[BETAB#Vragen]]


### HOOGSTEOPLTAB

![[HOOGSTEOPLTAB#Vragen]]

### SPOLIS

![[SPOLISBUS#Vragen]]

### RVU

![[RVU#Vragen]]

### LISS

![[LISS#Vragen]]