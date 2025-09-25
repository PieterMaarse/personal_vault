---
MOC: "[[_Home]]"
tags:
  - MOC
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]])
WHERE !contains(MOC, this.file.link)
```
---
## Notes
```dataview
TABLE about
WHERE contains(MOC, this.file.link)
```
