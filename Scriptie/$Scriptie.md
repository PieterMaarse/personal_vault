---
MOC: "[[_Home]]"
tags:
  - MOC
cssclasses:
---
---
## Inbox
```dataview
LIST
FROM [[]] and !outgoing([[]])
WHERE !contains(tags, "TODO") AND !contains(tags, "note") AND !contains(tags, "meeting") AND !contains(tags, "bron") AND !gearchiveerd
```
---
## TODO
```dataview
LIST
FROM !"_Obsidian"
WHERE !gearchiveerd AND contains(MOC, this.file.link) AND contains(tags, "TODO")
```
---
## Aantekeningen

#### Algemeen
```dataview
TABLE about
FROM !"_Obsidian"
WHERE contains(MOC, this.file.link) AND !gearchiveerd AND contains(tags, "note") AND contains(tags, "algemeen")
SORT file ASC
```

#### Inhoudelijk
```dataview
TABLE about
WHERE contains(MOC, this.file.link) AND contains(tags, "note") AND !gearchiveerd AND !contains(tags, "algemeen") AND inhoudelijk AND !contains(tags, "background")
```

#### Data
```dataview
TABLE about
WHERE contains(MOC, this.file.link) AND contains(tags, "note") AND !gearchiveerd AND !contains(tags, "algemeen") AND contains(tags, "data")
```

#### Praktisch
```dataview
TABLE about
WHERE contains(MOC, this.file.link) AND contains(tags, "note") AND !gearchiveerd AND !contains(tags, "algemeen") and !inhoudelijk and !contains(tags, "data")
```

#### Achtergrond
```dataview
TABLE about
WHERE contains(MOC, this.file.link) AND contains(tags, "note") AND !gearchiveerd AND contains(tags, "background")
```


---

## Meetings
```dataview
TABLE dateformat(date, "yyyy-LL-dd") AS date, discussed
WHERE contains(tags, "meeting") AND contains(MOC, this.file.link) and !gearchiveerd
SORT date DESC
```

---
## Bronnen

#### Base: [[Scriptie Bronnen Overzicht.base]]

![[Scriptie Bronnen Overzicht.base]]

#### Dataview
```dataview
TABLE WITHOUT ID rows.file.link[0] AS link, rows.type[0] AS type, rows.about[0] as about
FROM !"_Obsidian"
WHERE !gearchiveerd AND contains(MOC, this.file.link) AND contains(tags, "bron")
GROUP BY file.link
SORT rows.type ASC
```


---
## Archief

```dataview
TABLE tags, about
WHERE contains(MOC, this.file.link) AND gearchiveerd
SORT tags ASC
```
