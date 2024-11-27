---
{"dg-publish":true,"permalink":"/network/tailscale-o-auth-scope-for-docker/","tags":["public","tailscale","network","zerotrust"],"noteIcon":"1"}
---

```
Status: 403, Message: "calling actor does not have enough permissions to perform this function"
```
When following the docs form #tailscale for setting up docker for tailscale, you will encounter this error. 
This is because the scope for the OAuth tokens have been changed, 
the new correct scope is `auth_keys:write`


ref:
[Contain your excitement: A deep dive into using Tailscale with Docker](https://tailscale.com/blog/docker-tailscale-guide)