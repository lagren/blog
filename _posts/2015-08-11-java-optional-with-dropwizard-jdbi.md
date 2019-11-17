---
author: Eirik Tenold
date: 2015-08-11T15:35:00Z
tags:
- Dropwizard
- JDBI
- Java 8
title: How to use java.util.Optional with Dropwizard and JDBI
---

In order to use Java 8's java.util.Optional together with Dropwizard and JDBI, first include the Java 8 build of JDBI module:

In pom.xml (use version corresponding with Dropwizard):

{{< highlight xml >}}
<dependency>
	<groupId>io.dropwizard.modules</groupId>
	<artifactId>dropwizard-java8-jdbi</artifactId>
	<version>0.7.1-1</version>
</dependency>
{{< / highlight >}}

In the main application, make sure that you import the correct DBIFactory from the module:

{{< highlight java >}}
import io.dropwizard.java8.jdbi.DBIFactory;
{{< / highlight >}}
