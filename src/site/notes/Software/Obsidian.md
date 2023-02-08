---
{"dg-publish":true,"permalink":"/software/obsidian/","tags":["public"]}
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
- 

## Git sync obsidian

To rollback when a "wrong" sync happens use 

```bash
git revert CommitIdOfWrongCommit
```
Then, remove the local copy of files in obsidian, and recreate the vault and setup the sync again.