---
author: Eirik Tenold
title: How to trigger a Jenkins build from command-line
tags:
- Java
- Jenkins
---

To trigger a Jenkins build from command-line is pretty simple. In *nix, you can use wget to trigger the build 
via a HTTP request. If you don't have that kind of tool available on your platform (e.g. Windows), the CLI-client 
is a useful option.

First you need to download the client jar file; you can get this from http://&lt;your Jenkins server&gt;/cli. 
Place the jar file in an accessible location.

To start the build, just issue the command:

    java -jar jenkins-cli.jar -s http://<your Jenkins server>/ build <project name>