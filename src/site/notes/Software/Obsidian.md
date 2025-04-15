---
{"dg-publish":true,"permalink":"/software/obsidian/","tags":["public"],"noteIcon":"1"}
---

## About
Obsidian is a notetaking and scond brain tool
https://obsidian.md/

## Useful links

- https://dg-docs.ole.dev/ -> Digital garden info
- https://dannb.org/blog/2022/obsidian-daily-note-template/ -> Daily note template [[_Dailys/_template\|_template]]
- https://help.obsidian.md/How+to/Use+callouts -> Callouts
- https://github.com/kmaasrud/awesome-obsidian -> Awesome list!
- live sync plugin https://github.com/vrtmrz/obsidian-livesync/
	- couchdb server setup https://github.com/vrtmrz/obsidian-livesync/blob/main/docs/setup_own_server.md
- [GitHub - dartungar/obsidian-emotion-picker: Plugin for Obsidian.md that provides an easy way to insert emotions from a customizeable list.](https://github.com/dartungar/obsidian-emotion-picker) 
- [GitHub - tadashi-aikawa/obsidian-various-complements-plugin: This plugin for Obsidian enables you complete words like the auto-completion of IDE.](https://github.com/tadashi-aikawa/obsidian-various-complements-plugin) fantastisk autocomplete til [[Software/Obsidian\|Obsidian]] 

## Git sync obsidian

To rollback when a "wrong" sync happens use 

```bash
git revert CommitIdOfWrongCommit
```
Then, remove the local copy of files in obsidian, and recreate the vault and setup the sync again.

## graph view

#### Exclude a specific folder from graph view
In the graph view, under "Filters", type

```
-path:
```

Then you can either continue typing the name of the path or select it from the pop-up window that appears with all the paths in your vault. Once you select a path it will be excluded from your graph view (because of the minus sign)