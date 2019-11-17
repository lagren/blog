---
author: Eirik Tenold
date: 2011-07-03T20:51:00Z
modified_time: 2011-07-03T20:51:13.934+02:00
tags:
- VirtualBox
- Ubuntu
title: How to install Ubuntu 11.04 in VirtualBox
---

I wanted to have a clean environment where I could try different things and decided to install 
[VirtualBox](http://www.virtualbox.org/) on my desktop.

To install the host software under Ubuntu was easy. Just a simple apt-get command:

    sudo apt-get install virtualbox-ose
    
The installation of the guest OS was easy enough, just point and click. But when I tried to install 
the guest additions (so that the guest OS could access folders on the host) the guest OS would not boot 
up again. This happened a few times and the result was reinstall the guest OS. Next time I will 
remember to take a snapshot just after the install finishes.

After a simple google search, I found a 
[blog entry](http://flnkr.com/2011/04/29/installing-virtualbox-guest-additions-on-ubuntu-11-04/) on how 
to install the guest additions via apt-get:

    sudo apt-get update
    sudo apt-get install virtualbox-ose-guest-utils