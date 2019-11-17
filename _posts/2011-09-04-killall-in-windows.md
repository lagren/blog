---
author: Eirik Tenold
title: killall in Windows
tags:
- Windows
---

Recently I ran into a serious annoyance while using a Windows computer at work. Something triggered a 
cascade of processes that crashed and spawned other Dr Watson-threads. This bugged down my computer enough to be 
pain in the ass, and I didn't want to use the reset button on my computer, so I opened the Task Manager and 
looked for something that resembled *killall* from Unix. No such luck.

Once more Google provided me with a solution. How-to Geek had written an 
[article](http://www.howtogeek.com/howto/windows-vista/how-do-i-kill-all-the-iexploreexe-processes-at-once/) about the taskkill utility in Windows:

    taskkill /F /IM <processname.exe> /T