---
{"dg-publish":true,"permalink":"/software/jenkins/disable-access-control-in-jenkins/","tags":["public"],"noteIcon":"1","created":"","updated":""}
---


Administrators may accidentally set up a security realm or authorization strategy in such a way that they are no longer able to administer or even access Jenkins.

When this happens, there are ways to reset the access control configuration to allow anyone to administer Jenkins. The exact steps to do this depend on how you manage the Jenkins configuration. The sections below explain how to disable access control in multiple different ways.

After applying the advice below, Jenkins will be in an entirely unsecured mode after it starts, allowing anyone full access. If you are able to, consider making Jenkins accessible only by you while the configuration is being reset.

One way to do this is to make sure that Jenkins is only accessible from the server it is running on. If Jenkins is run using the built-in Winstone/Jetty container, set the `--httpListenAddress` or `--httpsListenAddress` (depending on whether you previously set up HTTPS in Winstone/Jetty) to `127.0.0.1`. Where to change this depends on how you installed Jenkins. Look up the documentation for your package or installer.

## Using `config.xml`[](https://www.jenkins.io/doc/book/security/access-control/disable/#using-config-xml)

Use these instructions if your Jenkins configuration is _not_ managed using Configuration as Code plugin or [Groovy Init Hooks](https://www.jenkins.io/doc/book/managing/groovy-hook-scripts/).

The following steps will delete the configuration for security realm and authorization strategy. Make sure you have a backup, to be able to restore the configuration to as close to the original state (except one where you’re not locked out) as possible.

1.  Stop Jenkins.

2.  Go to the Jenkins home directory.

3.  Open the file `config.xml` in this directory in a text editor. Make sure you use an editor that supports Unix line breaks.

4.  Look for the `<useSecurity>true</useSecurity>` element in this file.

5.  Look for the elements `<securityRealm>` and `<authorizationStrategy>` and remove them. Either may span multiple lines, delete everything up to and including `` </securityRealm>` `` and `</authorizationStrategy>`, respectively.

6.  Replace `true` with `false`.

7.  Start Jenkins.
