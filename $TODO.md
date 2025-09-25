---
MOC:
  - "[[_Home]]"
tags:
  - MOC
  - TODO
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
```
---
## TODOs
```dataview
LIST
FROM !"_Obsidian"
WHERE contains(tags, "TODO") AND !contains(file.link, this.file.link)
```
