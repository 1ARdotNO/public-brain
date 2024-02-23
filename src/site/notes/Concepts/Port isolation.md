---
{"dg-publish":true,"permalink":"/concepts/port-isolation/","tags":["public"],"noteIcon":"1","created":"2023-08-15T14:20:20.000+02:00","updated":"2022-12-23T10:22:06.000+01:00"}
---

#wifi #networking #unifi

A feature that can be enableed on network switch on a port by port basis.
Any device connected to a port with port isolation enabled may only forward traffic to other ports that do NOT have port isolation enabled.


You can even isolate clients effectively across multiple switches (e.g. access through aggregation) so long as you don’t isolate uplink ports. This will allow isolated clients to pass traffic out to the Internet, while preventing clients connected to upstream switches from accessing clients downstream.
![Pasted image 20221125115954.png](/img/user/Concepts/attachments/Pasted%20image%2020221125115954.png)
_Uplink pathways are green; isolated port pathways are orange. In this deployment scenario, all clients are isolated from one another, but can reach the Internet._

In summary, port isolation allows easy, one-click separation of client traffic at the VLAN edge. It allows groups of clients to be logically grouped into a single VLAN (e.g. “Guest”), but keeps their traffic fenced off so that snooping and tampering can be avoided—a win-win scenario!

source: https://meraki.cisco.com/blog/2015/03/new-switch-feature-provides-port-isolation/