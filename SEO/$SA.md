---
MOC:
  - "[[_Home]]"
tags:
  - MOC
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
WHERE !contains(MOC, this.file.link)
```
---
## SA Projecten
```dataview
LIST
WHERE contains(MOC, this.file.link) AND !contains(tags, "meeting") AND !contains(tags, "note")
```

## Algemene Aantekeningen
```dataview
LIST
WHERE contains(MOC, this.file.link) AND contains(tags, "note")
```

## Algemene Meetings
```dataview
TABLE meeting_with, discussed
WHERE contains(tags, "meeting") AND contains(MOC, this.file.link)
```
