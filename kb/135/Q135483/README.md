---
layout: page
title: "Q135483: Windows 95 CD-ROM Display.txt File"
permalink: /kb/135/Q135483/
---

## Q135483: Windows 95 CD-ROM Display.txt File

{% raw %}

	Article: Q135483
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains a copy of the information in the Display.txt file from the
	Windows 95 CD-ROM. Setup copies this file to the Windows folder.
	
	MORE INFORMATION
	================
	
	-------------------------------------------------------------------
	            Microsoft Windows 95 README for Displays
	                            August 1995
	-------------------------------------------------------------------
	
	            (c) Copyright Microsoft Corporation, 1995
	
	This document provides complementary or late-breaking information
	to supplement the Microsoft Windows 95 documentation.
	
	------------------------
	How to Use This Document
	------------------------
	
	To view Display.txt on screen in Notepad, maximize the Notepad
	window.
	
	To print Display.txt, open it in Notepad or another word
	processor, and then use the Print command on the File menu.
	
	--------
	CONTENTS
	--------
	
	DISPLAY ADAPTERS AND MONITORS
	Adapter Type
	Monitor Type
	Refresh Rates
	Correcting Display Problems
	Cursor Colors
	PCI Display Adapters
	IRQ Conflicts with PCI Display Adapters
	Avance Logic Display Adapters
	Diamond Stealth and Speedstar 64/Pro
	Diamond Viper
	S3 Display Adapters
	ATI Mach8/32/64
	Number Nine Imagine 128
	Hercules Graphite, Boca Vortek, Orchid Celsius (IIT AGX)
	Chips and Technologies
	IBM ThinkPad
	Matrox MGA
	Trident Display Adapters
	Video Logic 928Movie
	Western Digital
	SPEA Adapters
	Appian Renegade
	Compaq Presario with Cirrus Logic
	---------------------------------
	
	DISPLAY ADAPTERS AND MONITORS
	=============================
	
	Adapter Type
	------------
	Windows 95 Setup configures your adapter type based on the type of
	controller it uses; for example, S3, Cirrus Logic, or ATI. However,
	you may find a more exact match for your adapter make and model in
	Display properties. To change your adapter type, open Display
	properties, click the Settings tab, and then click Change Display
	Type. In the Adapter Type area, click Change.
	
	In most cases, selecting a more precise adapter type does not change
	the driver or its behavior in any way.
	
	Monitor Type
	------------
	If Windows 95 does not contain your exact monitor type, select one
	of the standard display types instead. This will not adversely affect
	the performance or quality of Windows 95 display output.
	
	Refresh Rates
	-------------
	Selecting your monitor type in Windows 95 Display properties does not
	affect the refresh rate used by your display adapter. To adjust the
	refresh rate, you must specify your monitor type in the adapter setup
	program supplied by your display adapter or PC manufacturer. Some
	utilities must be included in your Autoexec.bat file. On some PCs,
	monitor type is set in BIOS configuration programs. Examples of
	utilities from adapter manufacturers include:
	
	 ATI                   Install.exe
	 Cirrus Logic          Montype.exe, Clmode.exe
	 Diamond Stealth       Stlmode.exe
	 Diamond Stealth 64    S64mode.exe, go95.exe
	 Matrox                \Mga\Setup\Setup.exe
	 Tseng Labs            Vmode.exe
	 Western Digital       Vgamode.exe
	
	You may be able to obtain updated drivers that set the refresh rate
	based on the selected monitor type from adapter vendors or from the
	Windows Driver Library.
	
	Correcting Display Problems
	---------------------------
	In general, you can correct many display-related problems by clicking
	the Graphics button on the Performance tab in System properties. Drag
	the slider in this dialog box and experiment with different settings
	before you revert to 640x480 16-color mode to work around a problem.
	
	In particular, if you have problems with "see through" dialogs, or
	if graphic elements remain on your screen after you close a menu or
	dialog box, move the slider down one notch to "Most accelerator
	functions". This symptom can occur even on non-accelerated adapters.
	
	NOTE: Adobe Type Manager (ATM) is not compatible with the "None"
	setting in this dialog box. If Windows does not start due to this
	problem, restart Windows, and then press F8 when "Starting Windows 95"
	appears on your screen. Press 3 to start Windows in Safe Mode. Then
	change graphics acceleration to a different setting.
	
	Color Cursors
	-------------
	Color cursors require a Windows 95 display driver running at 256 or
	more colors. They are not supported for ATI mach8 display adapters.
	
	If Windows 95 is not using 32-bit disk access, cursors will not
	animate. You can check this setting in System properties on the
	Performance tab.
	
	PCI Display Adapters
	--------------------
	Your screen resolution may revert to 640x480 when Setup starts
	Windows 95 for the first time. Resolution should return to your usual
	settings in subsequent sessions.
	
	IRQ Conflicts with PCI Display Adapters
	---------------------------------------
	If your PCI display adapter is configured by your BIOS to use IRQ 15
	and a functioning secondary PCI IDE disk controller is also configured
	to use IRQ 15 (by default), Windows 95 assigns IRQ 15 to the IDE disk
	controller. This forces your display adapter to use VGA mode.
	
	To load the accelerated Windows 95 driver for your display adapter,
	you must eliminate the resource conflict. One of the following methods
	should work for you:
	
	- Obtain a BIOS upgrade from your hardware vendor.
	- If your BIOS supports it, disable the secondary PCI IDE controller
	 in the BIOS and on the Device Manager tab in System properties.
	- If your BIOS supports it, disable the IRQ of the display adapter.
	- If your BIOS supports it, manually reconfigure the display adapter
	 to use a different IRQ setting.
	
	Avance Logic Display Adapters
	-----------------------------
	A Windows 95 driver for Avance Logic 2301 adapters (for example, the
	Hercules Stingray adapter) is available on the Windows 95 CD-ROM in
	the \Drivers\Display\Avance folder.
	
	The driver is also available in the Windows Driver Library. For more
	information, see the Windows Driver Library section earlier in this
	file.
	
	Diamond Stealth and SpeedStar 64/Pro
	------------------------------------
	If you have the Windows 95 CD-ROM, enhanced drivers for these adapters
	are available in the \Drivers\Display\Diamond folder. These enhanced
	drivers enable you to set refresh rate based on the monitor type
	selected in Display properties. For more information about how to
	install these drivers, see the Readme.txt file.
	
	These drivers are also available in the Windows Driver Library. For
	more information, see the Windows Driver Library section earlier in
	this file.
	
	Diamond Viper
	-------------
	Windows 95 does not have a built-in driver for Diamond Viper adapters.
	However, if you install Windows 95 in the directory that contains your
	Windows 3.x files, Setup will preserve and use the drivers that are
	already there. If you install Windows 95 in a different directory,
	Setup will install the VGA driver.
	
	If you have the Windows 95 CD-ROM, a Windows 95 driver for Diamond
	Viper VLB and PCI adapters (Weitek P9000 based) is available in the
	\Drivers\Display\Diamond folder. For more information about how to
	install these drivers, see the Readme.txt file.
	
	These drivers are also available in the Windows Driver Library. For
	more information, see the Windows Driver Library section earlier in
	this file.
	
	S3 Display Adapters
	-------------------
	S3 adapters conflict with COM4 ports and modems. If you have modem
	problems using this configuration, change your modem to a different
	COM port. Or open System properties in Control Panel, click the
	Performance tab, click Graphics, and then drag the slider to None.
	
	You can correct certain S3 display problems by adding one of the
	following lines to the [Display] section of your System.ini file,
	which is located in the folder that contains your Windows 95 files.
	
	For problems with line and shape outline appearance, add:
	 Polygon=0
	
	For color problems with "High Color (16 bit)," add:
	 HighColor=15
	
	For color problems with "True Color (24 bit)," add:
	 TrueColor=24
	
	NOTE: The Windows 95 S3 driver supports 24-bit mode only at a
	resolution of 640 x 480.
	
	ATI Mach8/32/64
	---------------
	Windows 95 cannot use high-resolution modes properly unless your
	adapter is configured correctly using the ATI Install.exe program.
	
	Choosing the correct setting for your monitor type is especially
	important. Otherwise, high-resolution modes may not be available,
	or your computer may stop responding when it attempts to switch to
	them.
	
	If your computer occasionally stops responding on PCI mach32 or mach64
	adapters, try adding the line "outengine=0" to the [display] section
	of your System.ini file. The file is located in the folder that
	contains your Windows 95 files. If this does not work, try adding
	"VAD=1" in the same location.  This switch disables linear framebuffer
	mode, which can cause problems on some computers.
	
	Number Nine Imagine 128
	-----------------------
	A driver for this adapter is available from the Windows Driver
	Library. Windows 95 will install and use the Cirrus Logic driver for
	these adapters by default--limiting the maximum display settings to
	800x600, 256 colors. For more information, see the Windows Driver
	Library section earlier in this file.
	
	Hercules Graphite, Boca Vortek, Orchid Celsius (IIT AGX)
	--------------------------------------------------------
	The Windows 95 Setup program does not automatically install the driver
	for these adapters and other adapters that use the IIT AGX controller.
	To manually change to the correct display type, open Display
	properties in Control Panel, click the Settings tab, and then click
	Change Display Type.
	
	This will install the correct driver files, and enable you to select
	256-color, 16-bit color, and high-resolution modes.
	
	Chips and Technologies
	--------------------
	This driver is not installed by default on some laptop computers,
	including the Zenith 433. To manually install the correct driver, open
	Display properties in Control Panel, click the Settings tab, and then
	click Change Display Type.
	
	IBM ThinkPad
	------------
	To run resolutions above 640x480, you must configure your ThinkPad
	correctly. Check the ThinkPad utilities supplied by IBM; these are
	usually located on the Start menu.
	
	Some older ThinkPad models require that the Ibmvesa.com driver be
	loaded by your Autoexec.bat file during startup for 256-color modes
	to work.
	
	If you have a ThinkPad 755cx, open Display properties, click the
	Settings tab, and then click Change Display Type. Change your display
	type from "Western Digital" to "IBM ThinkPad 755cx." This will allow
	the built-in panel to display 800x600 modes and may correct some
	cursor-related problems.
	
	Matrox MGA
	----------
	For proper operation, your adapter and monitor settings must be
	correct in the Matrox setup utility, which is usually located on
	your hard disk in the \Mga\Setup folder. If your computer stops
	responding during startup, it may be caused by a conflict with a
	network adapter.
	
	If you encounter text problems--for example, incorrect or "garbage"
	characters--try adding "FontCache=OFF" to the [mga.drv] section of
	your System.ini file, which is located in the folder that contains
	your Windows 95 files.
	
	Trident Display Adapters
	------------------------
	If you have the Windows 95 CD-ROM, an enhanced driver for Trident
	Super VGA and accelerator adapters is available in the
	\Drivers\Display\Trident folder.
	
	This driver is also available in the Windows Driver Library. For more
	information, see the Windows Driver Library section earlier in this
	file.
	
	Video Logic 928Movie
	--------------------
	For 16-bit color modes to work correctly, make sure your display
	adapter type is set to "Video Logic 928Movie" in Display properties.
	
	Western Digital
	---------------
	On some laptop computers, the mouse pointer may change to a wide band
	of colored dots when you switch from a command prompt or MS-DOS-based
	program. To correct this problem, carry out the following procedure.
	
	1. Click the Start button, and then point to Settings.
	2. Click Control Panel, and then double-click the System icon.
	3. Click the Performance tab, and then click Graphics.
	4. Drag the slider to the left one notch.
	
	SPEA Adapters
	-------------
	On some SPEA adapters that use an S3 controller, your Autoexec.bat
	file must load a VESA TSR (for example, V7mepvbe.exe) for the
	Windows 95 S3 driver to work.
	
	Appian Renegade
	---------------
	Windows 95 Setup installs the VGA driver for this adapter. You can
	use Windows 3.1 Renegade drivers with Windows 95, but you must turn
	off the Device Bitmaps option so the drivers will operate properly.
	
	Compaq Presario with Cirrus Logic
	---------------------------------
	If your Compaq Presario uses the Windows 95 Cirrus Logic driver and
	is unable to use screen resolutions higher than 640x480, check your
	Autoexec.bat file for a line similar to the following:
	
	c:\windows\vgautil\clmode.exe t640=60 t800=0 t1024=0 t1280=0
	
	This line indicates that 800x600, 1024x768, and 1280x1024 resolutions
	are disabled because their refresh rates are set to 0. Only 640x480,
	60 Hz is enabled. If your monitor supports higher resolutions, carry
	out the following procedure (do not modify your Autoexec.bat file
	directly).
	
	1. Click the Start button, and then click Shut Down.
	2. Click Restart The Computer, and then click Yes.
	3. When the text "Starting Windows 95" appears, press and release
	  the F8 key.
	4. Select Command Prompt Only, and then press ENTER.
	5. At the command prompt, type the following:
	
	  c:\windows\vgautil\clmode
	
	6. Use the Clmode program to configure your monitor type
	appropriately.
	7. Quit the Clmode program, and then restart your computer.
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
