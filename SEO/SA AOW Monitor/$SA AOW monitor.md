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
WHERE !contains(MOC, this.file.link) OR !contains(tags, "note")
```
---
## Aantekeningen
```dataview
LIST
WHERE contains(MOC, this.file.link) AND contains(tags, "note")
```
