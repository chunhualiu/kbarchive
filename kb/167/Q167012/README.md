---
layout: page
title: "Q167012: INFO: Setting Control Panel Tools to Start After Unattended Setu"
permalink: /kb/167/Q167012/
---

## Q167012: INFO: Setting Control Panel Tools to Start After Unattended Setu

{% raw %}

	Article: Q167012
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbsetup kbOPK kbSBK
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	As discussed in the Microsoft Windows NT Workstation Deployment Guide,
	Unattend.txt and Sysdiff.exe cannot be used to preinstall sound cards and
	hardware devices. These devices must be installed after installation has been
	completed. To install devices during setup, the commands must be placed in the
	Cmdlines.txt file.
	
	However, by using the runonce key in the registry, you may set up various Control
	Panel tools so that they will start after the first time a workstation has
	logged on so that the administrator may add sound cards and tape drives. You can
	also place the entries in the Cmdlines.txt file so that the desired Control
	Panel tools will start during the installation of Windows NT.
	
	MORE INFORMATION
	================
	
	For detailed instructions on using the Runonce option, consult the Microsoft
	Windows NT 4.0 Deployment Guide, Chapter 5, and refer to the section on
	"Executing a Batch File on First Logon to Customize Windows NT." The Deployment
	Guide may be viewed from the following Web site:
	
	  http://www.microsoft.com/ntworkstation/technicalresources/deployment/DeploymentDocs/DownGuideAutomate.asp.
	
	To have the Multimedia tool under Control Panel automatically start when logging
	on, place the following line in the runonce key:
	
	     "Multimedia"="rundll32.exe shell32.dll,Control_RunDLL mmsys.cpl,@0"
	
	NOTE: Multimedia is the value name, the data type is REG_SZ and the value is
	rundll32.exe and so on. The syntax is the same for each of the following lines.
	
	To have the Multimedia tool start up when logging on, place the following line in
	the runonce key:
	
	     "Soundcard"="rundll32.exe shell32.dll,Control_RunDLL mmsys.cpl,@0,4"
	
	To have the SCSI tool start up when logging on, place the following line in the
	runonce key:
	
	     "SCSI"="rundll32.exe shell32.dll,Control_RunDLL devapps.cpl,@1"
	
	To have the Tape tool start up when logging on, place the following line in
	runonce:
	
	     "Tape"="rundll32.exe shell32.dll,Control_RunDLL devapps.cpl,@2"
	
	To have the Server tool start up when logging on, place the following line in
	runonce:
	
	     "Server"="rundll32.exe shell32.dll,Control_RunDLL srvmgr.cpl,@0"
	
	To have the Services tool start up when logging on, place the following line in
	runonce:
	
	     "Services"="rundll32.exe shell32.dll,Control_RunDLL srvmgr.cpl,@1"
	
	To have the Devices tool start up when logging on, place the following line in
	runonce:
	
	     "Devices"="rundll32.exe shell32.dll,Control_RunDLL srvmgr.cpl,@2"
	
	The above examples are not a complete list of all Control Panel tools that may be
	automatically started. Notice that SCSI and Tape share a common .cpl file,
	devapps.cpl, but have different ending parameters.
	
	To test other .cpl files (including third party), you can copy and paste the
	Rundll32.exe segment from the above lines to the Start \ Run command line. For
	example, the following line will bring up the Add/Remove tool:
	
	     "rundll32.exe shell32.dll,Control_RunDLL Appwiz.cpl,@0,1"
	
	Changing the last number from one to two will open the Add/Remove tool with the
	Windows NT Setup tab selected.
	
	To keep the unattended setup unattended, you can add these lines to a batch file
	or other script added to the runonce key, as well as a macro or other script.
	
	For related information on this topic, please see the following Knowledge Base
	articles:
	
	  Q135068 How to Start a Control Panel Tool in Windows 95
	
	  Q158447 How to Run a Program Only Once After Unattended Setup of NT 4.0
	
	  Q157361 How to Automatically Log On After an Unattended Setup
	
	  Q149648 Description of Control Panel (.cpl) Files
	
	For additional information on Windows NT 4.0 deployment/unattended installation,
	consult the Microsoft Knowledge Base at http://www.microsoft.com/kb and download
	the Windows NT 4.0 Deployment Guide from
	http://www.microsoft.com/ntworkstation/technical/DeploymentDocs/default.asp.
	
	Additional query words: Soundcard sb16 Tapedrive card Unattended Setup
	
	======================================================================
	Keywords          : kbsetup kbOPK kbSBK 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
