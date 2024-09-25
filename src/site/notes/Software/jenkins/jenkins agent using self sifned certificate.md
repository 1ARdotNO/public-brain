---
{"dg-publish":true,"permalink":"/software/jenkins/jenkins-agent-using-self-sifned-certificate/","tags":["public"],"noteIcon":"1","created":"2024-08-03T14:52:57.937+02:00","updated":"2023-03-14T14:39:41.000+01:00"}
---

WHen running jenkins agent using aself signed certificate on a host you can make the agent ignore the cerificate check by adding the argument `-noCertificateCheck ` to execution in the config.xml

> [!DANGER]
> This can be a security risk! either secure your endpoint some other way, or be SURE you are in control of the DNS or ip you connect to.
