---
{"dg-publish":true,"permalink":"/linux/dns-settings/","tags":["public"],"noteIcon":"1","created":"2022-12-23T10:22:06.307+01:00","updated":"2022-12-23T10:22:06.308+01:00"}
---

#dns #linux 

This is based on debian, but is similar in most distros

Open the config file
`nano /etc/resolv.conf`

Add entries, for search domain, and for nameservers. The list can contain multiple entries, and is read from top to bottom.
`search domain.local`
`nameserver 8.8.8.8`