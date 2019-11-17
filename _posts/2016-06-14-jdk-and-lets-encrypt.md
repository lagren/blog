+++
date = "2016-06-14T11:18:07+02:00"
title = "How to get Java to accept Let's Encrypt certificates"
tags = ["Let's Encrypt", "TLS", "PKI", "Java", "JRE", "JDK"]
+++

If you try to connect to a website/webservice using HTTPS and get the following error message:

	sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target
	
Then you have to add a root certificate to the certstore.

In this example we will add Let's Encrypt root certificate to the certstore. First we need to download the certificate 
from a trusted source. Let's Encrypt has listed their certificates on their [website](https://letsencrypt.org/certificates/).
Download the Let’s Encrypt Authority X3 certificate in pem-format.

If you want to check which certificates are already installed you can issue the command *keytool -list -keystore /usr/lib/jvm/java-8-oracle/jre/lib/security/cacerts*

To install the new certificate, issue the following command (on a single line):

	keytool -import -noprompt -trustcacerts -alias letsencryptx3 -file <location of lets-encrypt-x3-cross-signed.pem> 
	-keystore /usr/lib/jvm/java-8-oracle/jre/lib/security/cacerts -storepass changeit

After this is done, restart the JVM and try again.

Note: This has to be done as root.
