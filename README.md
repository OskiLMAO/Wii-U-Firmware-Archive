# Welcome to my Wii U Firmware Archival Project!
Ill try to archive every Wii U firmware archive possible. (excluding 1.X.X because i dont think any wii u has it)

What i have for now:

European firmware:
5.5.5E

Japanese firmware:
5.5.5J

US firmware:
5.5.6U
5.5.5U

**I wanna thank [JeremKOYTB](https://github.com/JeremKOYTB/) for making an app that makes this project a bit more possible**

# Instructions:
**_I am not responsible for bricked Wii U's, dead SD cards, dead MLC's or SLC's. Please
do some research if you have any concerns about doing this to your Wii U.
YOU are choosing to make these modifications, and if you will point the finger
at me for messing up your Wii U, I will laugh at you.
If you do not want to make modifications to your console(you still need to
install ISFSHax on your console), use RedNAND._**

**1. Installing ISFSHax**  
        Make sure your sd card is in FAT32. go to https://isfsh.ax/ and press "Download".  
        Copy everything to the sd card.  
        Now if you use aroma, hold B while the gamepad is booting or when launching the H&S app.  
        A black and white menu should show up asking you to choose a payload, select fw_img_loader  
        If your console isnt modded, you can use the browser exploit.  
        Open the Browser and go to `wiiuexploit.xyz`, press on the `Run Exploit!`   
		**IMMEDIATELY** hold B until you see the payload menu. Select `fw_img_loader`.  
        	**Note: minute only outputs 1080p through HDMI, no picture on the gamepad, and nothing on the analog outputs.**  
        Some people reported that the screen output is not working for them when minute was loaded from the `recovery_menu`. If you made sure nothing else is the problem (right fw.img, TV supports 1080p HDMI), you can try following along blindly by pressing the appropriate buttons. Make sure to wait long enough between the presses, so the system has time to load. Without display output skip the first backup and go directly to Installing ISFShax.  
        If you already have an SLC backupm you can skip this.  
        Navigate to `Backup and Restore` (9 presses with the Power Button, press the eject button)  
        Press `Dump SEEPROM & OTP` (press the eject button, return to the menu with one press of either of the buttons)  
        Dump `SLC.RAW` (3 presses with the Power button, press the eject button, this can take a hot minute so please wait patiently, press the power button)  
        Return to main menu (28 power button presses, eject)  
        Choose `Boot ios.img` (6x Power, 1x Eject)  
        Now the ISFShax installer should launch (this takes a few seconds)  
        Follow the Instructions on the screen, the buttons are the same as in minute. (3x Eject, 1x Power, 3x Eject)  
        The console should now turn off.  
        If the install was successful the Wii U should directly start into minute and the power LED on the console will be purple, once you turn it on.  
        Dump the `SLC.RAW` again. This will overwrite the previous SLC.RAW file on the SD. This is required if you need to restore the SLC for unbricking, without loosing ISFShax. Keep that backup in a safe place.  
        If you skipped the first Backup also backup OTP and SEEPROM now.  

**2. Setting up RedNAND**  
 THIS WILL ERASE EVERYTHING ON THE SD CARD  
        You'll need a 64GB or larger sd card for a 32GB model, you'll need a 16GB or larger sd card for a 8GB model.  
        Boot Minute Menu and proceed with these instructions:  
        Navigate to `Backup and Restore` (9 presses with the Power Button, press the eject button)  
        Choose the `Format RedNAND` option (10 presses with the Power Button, press the eject button)  
        Press eject, and then again. Then press Power. Now it'll start dumping the SLC and SLCCMPT.  
        **When it starts dumping the MLC, remove the sd card and force power off your Wii U. We are doing this because we want no data in the MLC partition.**  
        Now open GParted (i assume you use Linux, ill add instructions for windows later TBD)  
        Plug in your SD card into your Computer.  
        Youll see one FAT32 partition and three Unknown partitions. The first(and the largest) partition will be MLC, format it as EXT4. Format the SLC(right under the MLC) as FAT16 with the LBA flag.   	Copy the ISFShax files back. Now make a folder called `wafel_install` on the FAT32 partition. and copy all the folders from the firmware archive you downloaded.  
	Download [this module](https://github.com/StroopwafelCFW/wafel_setup_mlc/releases) and put it in `/wiiu/ios_plugins/`. Lastly, make a folder called `minute` on the root of your Wii U's SD card.
        Now make a text file called "rednand.ini", and paste this into the text file. Save the text file and eject your SD card.

```
[partitions]
slccmpt=true
slc=true
mlc=true
[scfm]
disable=false
allow_sys=false

[disable_encryption]
mlc=false

[sys_mount]
mlc=false
```


**3. Installing and Booting the firmware.**  
Insert the SD card into your Wii U.  
Turn on your Wii U and navigate to `Backup and Restore.`  
Choose `Delete redNAND scfm.img.` Go back and enter `Patch (sd) and boot redNAND` (one press with the power button).  
Now wait for the Power LED to stop Flashing. Your Wii U gamepad might turn on while it installs the titles.  
After the Wii U installs all titles (you can tell by the power LED not blinking), force power off your Wii U and power it back on. When youll boot redNAND again, you will be in Setup.
