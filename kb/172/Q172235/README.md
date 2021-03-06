---
layout: page
title: "Q172235: Extraction Failed-Service Pack Setup Error When Loading SP3"
permalink: /kb/172/Q172235/
---

## Q172235: Extraction Failed-Service Pack Setup Error When Loading SP3

{% raw %}

	Article: Q172235
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kberrmsg kbsetup
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you load Service Pack 3 you may receive one of the following two pop- up
	error messages:
	
	  Extraction Error:
	
	  There is not enough space on the disk.
	
	-or-
	
	  Service Pack Setup Error:
	
	  Not enough available hard drive space to run Service Pack Setup. (30 MB
	  required, or 60 MB if also creating an uninstall directory).
	
	Your only option is to click OK. The Service Pack update process will halt.
	
	CAUSE
	=====
	
	The Service Pack executable file (nt4sp3_i.exe) is a self-extracting file that
	extracts itself to the TMP environment variable location. By default, this is
	set to %SystemDrive%\Temp. If the drive containing this path is near capacity,
	you will get the Extraction Error as the file is expanding to the temporary
	directory.
	
	Upon successful extraction, Update.exe is launched and will update the Windows NT
	directory that is determined by the WINDIR environment variable. By default,
	this is set to %SystemRoot%. If the drive containing the %SystemRoot% is low on
	space you will get the Service Pack Setup Error.
	
	RESOLUTION
	==========
	
	Extraction Error
	----------------
	
	Either free up approximately 60 megabytes of disk space (53.8 MB expanded) on the
	system drive or change the environment variable TMP to another drive that has
	enough storage space.
	
	To change the environment variable, perform the following steps:
	
	1. Click the Start button, point to Settings, and click Control Panel.
	
	2. Double-click the System icon, and then click the Environment tab.
	
	3. Select TMP from the User Variables list, and then type
	  <newdriveletter>:\Temp in the Value box.
	
	4. Click OK, restart your computer, and then try to apply the service pack.
	
	Service Pack Setup Error
	------------------------
	
	Free up either 30 or 60 megabytes of disk space depending on whether or you not
	you choose to create an uninstall directory.
	
	Additional query words: update
	======================================================================
	Keywords          : kberrmsg kbsetup 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
