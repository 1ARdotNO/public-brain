---
{"dg-publish":true,"permalink":"/linux/check-folder-space-usage/","tags":["public","linux","disk"],"noteIcon":"1","created":"2024-08-03T14:53:45.917+02:00","updated":"2022-12-23T10:22:06.000+01:00"}
---


To find the size of folders in a dir run
`sudo du -h --max-depth=1 / | sort -n -r`

Change '/' to whatever path you are interested in.

Also see [[Linux/ncdu\|ncdu]] application for a bit more user friendlyness for this kind of task