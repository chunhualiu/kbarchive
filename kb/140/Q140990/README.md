---
layout: page
title: "Q140990: Mixing NDIS 2.0 and NDIS 3.x in Docked and Undocked States"
permalink: /kb/140/Q140990/
---

## Q140990: Mixing NDIS 2.0 and NDIS 3.x in Docked and Undocked States

{% raw %}

	Article: Q140990
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): win95
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are using a portable computer with a PCMCIA network adapter that uses
	NDIS 2.0 (16-bit) drivers, the computer may stop responding (hang) or reboot
	when you try to start it while it is not docked in its docking station if the
	docking station contains a network card that is capable of using NDIS 3.x
	(32-bit) network adapter drivers.
	
	CAUSE
	=====
	
	When Windows 95 detects the NDIS 2.0 drivers for the PCMCIA network adapter, it
	forces the loading of NDIS 2.0 drivers for the other network adapter (which is
	not currently present because the computer is undocked).
	
	Because one of the network adapters is not present, an incomplete binding occurs,
	which can cause the computer to hang or reboot.
	
	
	RESOLUTION
	==========
	
	To enable Windows 95 to start whether the computer is docked or undocked, create
	a multiple-boot configuration.
	
	Do not perform this procedure until you have determined that you have a docked
	state that requires an NDIS 3.x driver to be loaded and an undocked state that
	requires an NDIS 2.0 driver to be loaded, or vice versa.
	
	If this is not the case, you need to perform other troubleshooting steps to
	resolve the problem.
	
	To create a multiple-boot configuration, follow all the steps in the following
	sections.
	
	Preparing for Multiple Configurations
	-------------------------------------
	
	1. Make a backup copy of the Config.sys and Autoexec.bat files.
	
	2. Restart the computer. When you see the "Starting Windows 95" message, press
	  the F8 key, and then choose Command Prompt Only from the Startup menu.
	
	3. Type the following line, and then press ENTER:
	
	  " md configs " (without the quotation marks)
	
	  You will use the new Configs folder for storing a temporary copy of the
	  registry files.
	
	Configuring the Network While Docked
	------------------------------------
	
	1. Dock your computer and then restart Windows 95 normally.
	
	2. Use the Network tool in Control Panel to configure the computer to use the
	  network adapter that is in the docking station. Use the NDIS 3.x protocols if
	  they are compatible. If not, set the network adapter to use NDIS 2.0 drivers.
	
	3. Restart the computer. When you see the "Starting Windows 95" message, press
	  the F8 key, and then choose Command Prompt Only from the Startup menu.
	
	4. Change to the Windows folder.
	
	5. Type the following lines. Press ENTER after each line:
	
	  " attrib -r -s -h system.dat " (without the quotation marks)
	
	  " copy/b system.dat c:\configs\system.dok " (without the quotation marks)
	
	  " copy protocol.ini c:\configs\protocol.dok " (without the quotation marks)
	
	Configuring the Network While Undocked
	--------------------------------------
	
	1. Undock the computer and then restart Windows 95 normally.
	
	2. Use the Network tool in Control Panel to remove the network adapter you
	  configured in step 2 above.
	
	3. Configure the network adapter for the undocked configuration. This is
	  typically a PCMCIA network adapter. If this adapter requires real-mode NDIS
	  2.0 drivers, install them now.
	
	4. Restart the computer. When you see the "Starting Windows 95" message, press
	  the F8 key, and then choose Command Prompt Only from the Startup menu.
	
	5. Change to the Windows folder.
	
	6. Type the following lines. Press ENTER after each line:
	
	  " attrib -r -s -h system.dat " (without the quotation marks)
	
	  " copy/b system.dat c:\configs\system.und " (without the quotation marks)
	
	  " copy protocol.ini c:\configs\protocol.und " (without the quotation marks)
	
	Enabling Multiple Configurations
	--------------------------------
	
	NOTE: The information in this section assumes that Windows 95 is installed in the
	Windows folder on drive C. If this is not the case, please adjust the following
	information accordingly.
	
	Use any text editor (such as Notepad or Edit.com) to edit the Autoexec.bat file.
	Add the following lines to the file:
	
	  set windir=c:\windows
	  choice/c:DU Docked or Undocked configuration
	  if errorlevel 2 goto docked
	  if errorlevel 1 goto undocked
	  goto end
	
	  :docked
	     cd %windir%
	     attrib -r -s -h system.dat
	     del system.dat
	     del protocol.ini
	     copy/b c:\configs\system.dok system.dat
	     copy c:\configs\protocol.dok protocol.ini
	     goto end
	
	  :undocked
	     cd %windir%
	     attrib -r -s -h system.dat
	     del system.dat
	     copy/b c:\configs\system.und system.dat
	     copy c:\configs\protocol.und protocol.ini
	     goto end
	
	  :end
	     rem all done
	
	After you add these lines, save and then close the Autoexec.bat file.
	
	When you restart your computer, the network adapter drivers will be processed
	after the Autoexec.bat file has been processed. Therefore, the networking
	components can be segregated into separate boot configurations without causing a
	problem.
	
	NOTE: Although this technique can be used for a variety of different situations,
	it should be used only in this case. All other situations requiring multiple
	configurations should be handled through the user interface using system
	profiles.
	
	REFERENCES
	==========
	
	For additional information about setting up multiple configurations,
	double-click the Help.com file in the Other\Oldmsdos folder on the Windows 95
	CD-ROM, and then click Multi-config on the Command References page.
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
