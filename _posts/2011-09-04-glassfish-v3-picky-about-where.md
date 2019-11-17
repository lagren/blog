---
author: Eirik Tenold
title: 'GlassFish v3: Picky about where the libraries in an EAR are located'
tags:
- GlassFish
- Java
- Java EE
- Maven
---

While trying to deploy an EAR-application on GlassFish v3, I got an error about missing class files. The mentioned 
class files where from external libraries packaged along with my EJB inside the ear-file. I found this strange since 
the same ear-file deployed just fine on GlassFish v2. Strange...

After a couple of hours with trial-and-error and my favorite troubleshooter (Google), I came across another guy who 
had [similar problems](http://stackoverflow.com/questions/4721793/how-to-deploy-a-library-with-java-ee-6-glassfish-3-x). 
It turned out that GlassFish v3 is more picky about where libraries are located. The short answer: Just add a simple 
line in the pom.xml:

	<library-directory>lib</library-directory>