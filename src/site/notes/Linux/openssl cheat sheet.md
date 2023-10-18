---
{"dg-publish":true,"permalink":"/linux/openssl-cheat-sheet/","tags":["public","linux","ssl"],"noteIcon":"1","created":"2023-08-15T14:20:38.000+02:00","updated":"2022-12-23T10:22:06.000+01:00"}
---

# Converting a PFX file to PEM and Key via openssl
Export the private key
`openssl pkcs12 -in aa.pfx -out aa.key -nocerts -nodes`

take out the encryption from the private key
`openssl rsa -in aa.key -out aa_s.key`

export the ssl cert (normal cases)
`openssl pkcs12 -in aa.pfx -out aa.pem -nokeys -clcerts`