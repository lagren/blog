---
author: Eirik Tenold
title: How to use a global ignore file in Mercurial
tags:
- Mercurial
---

I got tired of manually adding common elements to the .hgignore-file, so after some quick research the 
option for a global ignore file presented itself as the solution to my problem.

Just a few lines in the Mercurial user file is needed:

    [ui]
    ignore = C:\&lt;some path&gt;\mercurial.ignore

Example content for the ignore-file:

    target
    
This information is also available in the [user manual](http://www.selenic.com/mercurial/hgrc.5.html).