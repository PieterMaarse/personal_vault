---
MOC:
  - "[[$SA]]"
tags:
  - MOC
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
WHERE !contains(tags, "meeting") and (!contains(tags, "bron") and !contains(tags, "note"))
```
---
## TODO
```dataview
LIST
WHERE contains(MOC, this.file.link) AND contains(tags, "TODO")
```
---
## Aantekeningen
```dataview
TABLE about
WHERE contains(MOC, this.file.link) and contains(tags, "note") and !contains(tags, "TODO") and !contains(tags, "model") and !gearchiveerd
```
---
### Aantekeningen Modellen

- [[EC Modellen Canvas.canvas|EC Modellen Canvas]]
```dataview
TABLE about
WHERE contains(MOC, this.file.link) AND contains(tags, "model") and !gearchiveerd
```
---
## Meetings
```dataview
TABLE date, meeting_with, discussed
WHERE contains(tags, "meeting") AND contains(MOC, this.file.link) and !gearchiveerd
SORT date DESC
```
---
## Bronnen
```dataview
TABLE about
FROM !"_Obsidian"
WHERE !gearchiveerd AND contains(MOC, this.file.link) AND contains(tags, "bron")
```

---
## Archief

```dataview
TABLE tags, about
WHERE contains(MOC, this.file.link) AND gearchiveerd
SORT tags ASC
```
