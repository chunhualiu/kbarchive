---
layout: page
title: "Q129212: Problems Using Diamond Viper VLB Video Adapter"
permalink: /kb/129/Q129212/
---

## Q129212: Problems Using Diamond Viper VLB Video Adapter

{% raw %}

	Article: Q129212
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
	
	After you install Windows 95 on a computer with a Diamond Viper VLB video card
	and the Diamond Windows 3.1 video drivers, you may experience one or more of the
	following problems:
	
	- 16-color VGA is the only resolution listed.
	
	- You can use only one setting. For example, you can use only the 640 x 480 x
	  256 setting.
	
	- When you restart Windows 95 you receive an error messages stating that the
	  display adapter is not configured properly.
	
	CAUSE
	=====
	
	Windows 95 does not detect the Diamond Viper VLB video card (with the Weitek
	P9000 chip set), so it installs the standard VGA adapter driver.
	
	RESOLUTION
	==========
	
	There are Diamond-supplied Beta 32-bit video drivers on the Windows 95 CD-ROM in
	the Drivers\Display\Diamond folder. Please note that these are Beta drivers, and
	may not function correctly with all hardware. If you have the floppy disk
	version of Windows 95, you can obtain these drivers from Diamond directly. For
	information about obtaining these drivers from Diamond, please see the Viper.txt
	file.
	
	To resolve this problem, follow these steps:
	
	1. Click the Start button, point to Settings, then click Control Panel.
	
	2. Double-click the System icon.
	
	3. Click the Device Manager tab.
	
	4. Double-click Display Adapters, click Standard Display Adapter (VGA), then
	  click the Remove button.
	
	  NOTE: Do not restart your computer when you are prompted to do so.
	
	5. Double-click the Add New Hardware icon in Control Panel.
	
	6. Click Next, click the No button to select it, and then click Next.
	
	7. Click Display Adapters in the Hardware Types list, and then click Next.
	
	8. Click Have Disk, select the Drivers\Display\Diamond folder on the Windows 95
	  CD-ROM, and then install the appropriate Diamond Viper driver for your video
	  adapter.
	
	9. Shut down and restart your computer.
	
	  NOTE: You still need a Viper.ini file (created by Vprmode.exe) stored in the
	  C:\Viper folder or another location referenced by the "Set ViperPath="
	  statement in the Autoexec.bat file. After installing these beta drivers, you
	  cannot use the Windows 3.1 Diamond Install tool in Control Panel. It will
	  cause a general protection fault.
	
	MORE INFORMATION
	================
	
	
	After you remove the standard VGA adapter from Device Manager, you must use the
	Add New Hardware tool in Control Panel to add a new video adapter if you replace
	the Diamond Viper card.
	
	The third-party products discussed in this article are manufactured by a vendor
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: vesa local bus
	
	======================================================================
	Keywords          : win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
