+++
date = "2016-06-19T12:18:32+02:00"
title = "Extension pack must be reinstalled when VirtualBox is upgraded"
tags = ["VirtualBox"]
+++

Today I upgraded VirtualBox from 4.3 to 5.0 using apt. The upgrade worked almost seamlessly with any upgrade problems. But
when I restarted the VMs then I was unable to connect to the VM using remote desktop. After some searching I discovered
that I had to uninstall an extension pack and then reinstall it again.

First we have to download the [correct extension pack](https://www.virtualbox.org/wiki/Downloads) for the installed version of VirtualBox.

	wget "http://download.virtualbox.org/virtualbox/5.0.22/Oracle_VM_VirtualBox_Extension_Pack-5.0.22-108108.vbox-extpack"
	
Then we have to uninstall the old version and install the new one (after all VMs has been stopped):

	VBoxManage extpack uninstall "Oracle VM VirtualBox Extension Pack"
	VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-5.0.22-108108.vbox-extpack
	
After this was successfully done I could connect using remote desktop :-)