---
{"dg-publish":true,"permalink":"/programmering/appwrite-github-integration/","tags":["appwrite"],"noteIcon":"1"}
---


When setting up appwrite github integration I encountered an error relating to the github private key.

Turns out when setting the key in the .env file you must include \n at the end of each line, then merg it all to one line

applies to this variable,     
```
_APP_VCS_GITHUB_PRIVATE_KEY=
```

This youtube vidseo show specifically
[Site Unreachable](https://youtu.be/GFoxpT_RQj4?t=761)