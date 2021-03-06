---
layout: page
title: "Q166820: Unattended Install of PowerToys in WinNT Server Reskit 4.0"
permalink: /kb/166/Q166820/
---

## Q166820: Unattended Install of PowerToys in WinNT Server Reskit 4.0

{% raw %}

	Article: Q166820
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbsetup kbOPK kbSBK
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Windows NT Server 4.0 Resource Kit Supplement 1 includes four desktop
	components that are not included in the original Windows NT Server 4.0 Resource
	Kit.
	
	The new components are:
	
	     CMD Prompt Here (Cmdhere.inf)
	     Security        (Rshxmenu.inf)
	     Run             (Runext.inf)
	     TweakUI         (Tweakui.inf)
	
	The new components are located in the PowerToy directory under the resource kit
	directory. If you used the default to install the resource kit, the directory is
	C:\Ntreskit\Powertoy
	
	To manually install the new components, go to Windows NT Explorer and highlight
	the .inf file. Right-click and then click Install from the menu.
	
	MORE INFORMATION
	================
	
	To automate the installation of the Power Toys during deployment or unattended
	installation of Windows NT 4.0, you need an Unattend.txt file that is configured
	to install Windows NT 4.0. Follow these steps:
	
	1. Add the option OEMPreInstall = Yes to the [UNATTENDED] section in the answer
	  file.
	
	2. Create an I386 directory on a server and copy the files from the I386
	  directory of the Windows NT 4.0 compact disc to the I386 directory on the
	  server.
	
	3. Create a directory called $OEM$ under the I386 directory on the server.
	
	4. Copy the contents of the PowerToy directory to the $OEM$.
	
	        Cmdhere.inf
	        Rshxmenu.inf
	        Rshxmenu.X86
	        Runext.inf
	        Runext.X86
	        Tweakui.CNT
	        Tweakui.CPL
	        Tweakui.HLP
	        Tweakui.inf
	
	5. Use a text editor to create or modify the Cmdlines.txt file, and save it to
	  the $OEM$.
	
	To save time, you can copy the following 5 lines of information to create the
	required Cmdlines.txt.
	
	     [Commands]
	     "rundll32 setupapi,InstallHinfSection DefaultInstall 128 .\CMDHERE.INF"
	     "rundll32 setupapi,InstallHinfSection DefaultInstall 128 .\RSHXMENU.INF"
	     "rundll32 setupapi,InstallHinfSection DefaultInstall 128 .\RUNEXT.INF"
	     "rundll32 setupapi,InstallHinfSection DefaultInstall 128 .\TWEAKUI.INF"
	
	If you have an existing Cmdlines.txt file, do not copy the [Commands] line, as an
	existing Cmdlines.txt file has this line.
	
	1. A modification of the Tweakui.inf file in the $OEM$ directory is required to
	  prevent the Windows NT 4.0 installation from stopping. When the TweakUI
	  utility runs, a help file is displayed during installation. To disable the
	  help file, comment the following line in Tweakui.inf with a semicolon:
	
	        HKLM,%SMWCV%\RunOnce\Setup,%ITWEAK%,,"WINHLP32.EXE -i Main
	        %18%\TWEAKUI.HLP"
	
	Your Tweakui.inf should look like this after the semicolon is added:
	
	     HKLM,%SMWCV%\Run,%TWEAKUI%,,"RUNDLL32.EXE TWEAKUI.CPL,TweakMeUp"
	     HKLM,%SMWCV%\RunOnce\Setup,%UPTWEAK%,,"RUNDLL32.EXE
	        TWEAKUI.CPL,TweakMeUp 0";
	     HKLM,%SMWCV%\RunOnce\Setup,%ITWEAK%,,"WINHLP32.EXE -i Main
	        %18%\TWEAKUI.HLP"
	
	NOTE: The previous text should take up 3 lines. It has been wrapped for
	readability.
	
	Consult the Windows NT 4.0 Device Driver Kit (DDK) and the Windows NT 4.0
	Software Development Kit (SDK) for detailed information on the new INF format
	and options.
	
	For additional information on the Windows NT 4.0 Power Toys, consult the online
	documentation for Windows NT 4.0 Server Supplement 1.
	
	For additional information on Windows NT 4.0 deployment or unattended
	installation, consult the Microsoft Knowledge Base at
	http://www.microsoft.com/kb and download the Windows NT 4.0 Deployment Guide
	from http://www.microsoft.com/ntworkstation/.
	
	NOTE: The Deployment Guide is valid for both Windows NT Workstation and Windows
	NT Server.
	
	Additional query words: Install
	
	======================================================================
	Keywords          : kbsetup kbOPK kbSBK 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
