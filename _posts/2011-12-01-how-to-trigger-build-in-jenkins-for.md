---
author: Eirik Tenold
date: 2011-12-01T17:08:00Z
modified_time: 2011-12-01T17:13:51.673+01:00
tags:
- Java
- Mercurial
- Jenkins
title: How to trigger a build in Jenkins for each commit in Mercurial
---

Just add the following to the [hgrc file](http://www.selenic.com/mercurial/hgrc.5.html) in the project's 
hg directory:

    [hooks]
    commit.jenkins = java -jar <jenkins-cli.jar> -s http://<url>/ build -c <project name>
    
To get the jenkins-cli.jar file, follow the instructions in this [post](http://blog.relativt.net/2011/12/how-to-trigger-jenkins-build-from.html).
 
More information on [Mercurial hooks](http://hgbook.red-bean.com/read/handling-repository-events-with-hooks.html) can 
be found in [Mercurial: The Definitive Guide](http://hgbook.red-bean.com/).