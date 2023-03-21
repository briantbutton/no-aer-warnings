# Selectively turn off AER warnings

Certain low level hardware errors can recur at high frequency, blatting onto the screen and/or filling up your log files.&nbsp;
It has something to do with Advanced Error Reporting (AER) and PCI Express (PCIE).&nbsp;
I do not understand it at all, but this repo contains a way to selectively turn off AER warnings for a specific PCIE device.&nbsp;

Stack Overflow and Ask Ubuntu are full of posts where the suggested solution is simply to turn off AER or some other subsystem.&nbsp; 
Like this:&nbsp; 

	pci=noaer

or&nbsp; 

	pci=nomsi

This is a more selective mechanism that eliminates the need for such drastic measures.&nbsp;
It turns off *warnings*, not errors, and only for the named device.&nbsp;
AER continues to run unencumbered, as God intended.&nbsp;

This is entirely built on the magnificent gist posted by Brainiarc7, which explains the problem and solves it.&nbsp; 
https://gist.github.com/Brainiarc7/3179144393747f35e5155fdbfd675554&nbsp;


	service@ButtonNet0000010:/var/log$ sudo lshw -numeric -short | grep ":"
	/0/0                          bridge     Broadcom Inc. and subsidiaries [14E4:2711]
	/0/0/0                        storage    KIOXIA Corporation [1E0F:1]
	/1            usb1            bus        DWC OTG Controller [1D6B:2]
	/1/1                          bus        USB 2.0 Hub [1A40:101]
	/1/1/1                        bus        USB2.0 Hub [5E3:610]
	/1/1/1/1                      input      RPI Wired Keyboard 4 [4D9:6]
	/1/1/1/4                      input      USB Optical Mouse [93A:2510]
	/1/1/2                        generic    802.11ac NIC [BDA:B812]



