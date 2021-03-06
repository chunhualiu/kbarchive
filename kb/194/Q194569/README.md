---
layout: page
title: "Q194569: Installing Windows NT 4.0 Service Pack 4 from the Internet"
permalink: /kb/194/Q194569/
---

## Q194569: Installing Windows NT 4.0 Service Pack 4 from the Internet

{% raw %}

	Article: Q194569
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbFEA kbWinNT400sp4feakbfaq
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to install Windows NT 4.0 Service Pack 4 (SP4) from
	the Internet using a Web browser.
	
	MORE INFORMATION
	================
	
	To install Service Pack 4 from the Internet using a Web browser (such as
	Microsoft Internet Explorer 3.02 or later), visit either of the following Web
	sites:
	
	  http://support.microsoft.com/support/ntserver/content/servicepacks/
	
	  http://support.microsoft.com/support/downloads/
	
	Click the Install Service Pack 4 link to begin the installation process on the
	computer. These Web pages automatically detect which files need to be updated
	and then copy the appropriate files to a temporary folder on the computer. Only
	those files that are needed to update the computer are installed.
	
	NOTE: If you use a Web browser other than Internet Explorer 3.02 or later, this
	update method may not work properly. If you are unable to install the service
	pack using this method, download the entire service pack from the Internet to
	your computer, and then run the Update.exe installation program locally.
	
	This installation method detects the version of the current service pack on your
	computer by querying the registry with ActiveX components. A script, specific to
	the version of the service pack detected, copies all appropriate files to be
	updated from the Winnt folder to a randomly named folder on the volume with the
	most available disk space.
	
	The process then patches each of the appropriate files, running a cyclical
	redundancy check (CRC) calculation, to update them to the new SP4 level. If the
	CRC does not match what it expects (for example, if the file is a post- service
	pack hotfix or third-party-provided file), the script copies the newer file from
	a Microsoft Web server.
	
	When all files have been patched, there is a complete image of the service pack
	in the temporary folder. The installation program then runs as it would when it
	is copied to a hard disk or from a CD-ROM.
	
	NOTE: To obtain the latest service pack for Microsoft Windows NT version 4.0,
	please refer to the following article in the Microsoft Knowledge Base.
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	======================================================================
	Keywords          : kbFEA kbWinNT400sp4fea kbfaq
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	Hardware          : ALPHA x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
