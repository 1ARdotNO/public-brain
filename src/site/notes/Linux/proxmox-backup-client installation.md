---
{"dg-publish":true,"permalink":"/linux/proxmox-backup-client-installation/","tags":["public","proxmox","backup","linux"],"noteIcon":"1","created":"2023-08-15T14:20:14.000+02:00","updated":"2023-01-19T14:57:12.000+01:00"}
---

#proxmox 
# About

This page contains an excerpt for the installation of the proxmox-backup-client CLI utility.  
This reference is kept here for the sake of quick access and completeness.  
The source reference is: [https://pbs.proxmox.com/docs/installation.html#client-installation](https://pbs.proxmox.com/docs/installation.html#client-installation "https://pbs.proxmox.com/docs/installation.html#client-installation")

## Manual installation in Debian host

### Add repository

Add the following to `/etc/apt/sources.list`

`1deb http://download.proxmox.com/debian/pbs buster pbstest`

#### Install the client

`1# apt-get update 2# apt-get install proxmox-backup-client`