---
{"dg-publish":true,"permalink":"/linux/open-vpn-split-tunnel-client-side/","tags":["public","vpn"],"noteIcon":"1"}
---



### about
In the case where you need to enable split tunnel for OpenVPN, on a config file from a server that is pushing routes and redirecting all traffic to the gateway, you can modify the local config file to work around this.

### implementation


```
# add the line below to the config dfile with the network and subnet for the network you want to reach
route 10.10.0.0 255.255.0.0

```
