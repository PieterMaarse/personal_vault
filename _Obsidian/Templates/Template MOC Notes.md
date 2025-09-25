
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]]) and !"_Obsidian"
WHERE !contains(MOC, this.file.link)
```
---
## Notes
```dataview
LIST
WHERE contains(MOC, this.file.link)
```
