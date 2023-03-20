---
{"dg-publish":true,"permalink":"/software/jenkins/jenkins-agent-using-self-sifned-certificate/","tags":["public"],"noteIcon":"1","created":"","updated":""}
---

WHen running jenkins agent using aself signed certificate on a host you can make the agent ignore the cerificate check by adding the argument `-noCertificateCheck ` to execution in the config.xml

> [!DANGER]
> This can be a security risk! either secure your endpoint some other way, or be SURE you are in control of the DNS or ip you connect to.
