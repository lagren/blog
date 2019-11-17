---
title: How to install Guest Additions in a headless VM (VirtualBox)
tags: ["VirtualBox"]
---

The Guest Additions gives some performance benefits if these are installed in the guest OS. At home a run VirtualBox in
a headless set-up and this makes it impossible to use the GUI to install the guest additions.

<!--more-->

In order to fix this i first transfer the iso from the host to the guest

	scp /usr/share/virtualbox/VBoxGuestAdditions.iso <guest VM IP>:/tmp

Then I ran the following commands in the guest OS:

	mount /tmp/VBoxGuestAdditions.iso /media
	cd /media/
	./VBoxLinuxAdditions.run

Follow the instructions and enjoy! :-)