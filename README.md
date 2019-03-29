# wineadcp
A script to help install and configure RD Instruments WinADCP on linux and Mac

This script will copy the necessary files to the appropriate locations and it<br>
will use winetricks to install the windows dependencies.


Sceeenshots
===========
![WinADCP](winadcp_lxde.png?raw=true "WinADCP running on lubuntu 18.04")



Requirements
============

wine 1.6 or higher<br>
winetricks<br>
zenity

The following files are zero byte files used to create this script.
```
WADPOps.Txt
WinADCP.chm
WinADCP.exe
```

In order for this to work the listed files must be replaced with actual files created by RD Instruments.<br>
I created this script because I didn't have the WinADCP installer but I had an existing installation.<br>
you can copy these files from an existing installation on windows, overwrite these, and it will work.<br>

Make sure to use a 32 bit prefix. if your existing prefix is 64 bit then create a new one.<br>
eg.
``` bash
WINEPREFIX=~/.adcp WINEARCH=win32 winecfg
```
This creates a 32 bit prefix where the simulated file system is in $HOME/.adcp<br>
Make the install script executable and install to the .adcp prefix<br>
If no prefix is supplied then everything is installed in the default prefix $HOME/.wine
```bash
chmod +x install
./install ~/.adcp
```
Run The wine configuration program
```bash
WINEPREFIX=~/.adcp winecfg
```
* Click on Add application and navigate and select C:\Program Files\RD Instruments\WinADCP\WinADCP.exe<br>
* Under the Windows version drop down list select "XP"<br>
* Click on the libraries tab and enter "comctl32" in the New override for library field and click on Add.<br>
* Click on the Edit button and select "Built in then Native" and click on OK to close winecfg<br>

You should now be able to launch WinADCP from the launcher.
