---
layout: page
title: "Q207750: How to Prevent the Display of Control Panel Icons"
permalink: /kb/207/Q207750/
---

## Q207750: How to Prevent the Display of Control Panel Icons

{% raw %}

	Article: Q207750
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbenv kbEnableMove kbEnableLearn
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	To provide enhanced workstation security, network administrators may prevent the
	display of icons on Control Panel on specific computers using a Windows NT
	security policy template.
	
	MORE INFORMATION
	================
	
	A preconfigured policy template file can be created for this purpose. To create
	the policy file:
	
	1. Click Start, click Run, type "notepad" (without the quotation marks), and
	  then click OK.
	
	2. Type the following lines into the empty file. You can also use copy and paste
	  commands to place the text into the empty file:
	
	  CLASS USER
	
	  CATEGORY !!CPL_Icons
	  POLICY !!CPL_Access
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "Access.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Norton
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "S32LUCP1.CPL"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_AppWiz
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "appwiz.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Console
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "console.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Cpqmgt
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "cpqmgmt.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_DevApps
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "devapps.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Inetcpl
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "inetcpl.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Intl
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "intl.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Joy
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "Joy.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_License
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "liccpa.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Main
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "main.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_MonAgt
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "bhctrl.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_MMsys
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "mmsys.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Modem
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "modem.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_NCPA
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "ncpa.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_ODBC
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "odbccp32.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Ports
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "Ports.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Server
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "srvmgr.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_System
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "sysdm.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Telephony
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "telephon.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_Timedate
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "timedate.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_UPS
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "UPS.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_MAIL
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "MLCFG32.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_HARDWARE
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "hdwwiz.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_SCANNER
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "sticpl.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	
	  POLICY !!CPL_POWER
	  KEYNAME "Control Panel\Don't Load"
	  VALUENAME "powercfg.cpl"ValueOn !!CPL_Hide ValueOff Numeric 0
	  END POLICY
	  END CATEGORY; Control Panel
	
	  [strings]
	  CPL_Icons="Control Panel Icons"
	  CPL_Access="Deny Access to Accessibility"
	  CPL_Norton="Deny Access to Norton Live Update"
	  CPL_AppWiz="Deny Access to Add/Remove Programs"
	  CPL_Console="Deny Access to Console Properties"
	  CPL_Cpqmgt="Deny Access to Compaq Insight Agents"
	  CPL_DevApps="Deny Access to PC Card"
	  CPL_Inetcpl="Deny Access to Internet"
	  CPL_Intl="Deny Access to Regional Settings"
	  CPL_Joy="Deny Access to Joystick"
	  CPL_License="Deny Access to Licensing"
	  CPL_Main="Deny Access to Fonts,Mouse,Keyboard,Printers"
	  CPL_MonAgt="Deny Access to Monitoring Agent"
	  CPL_MMSys="Deny Access to Multimedia"
	  CPL_Modem="Deny Access to Modem"
	  CPL_NCPA="Deny Access to Network"
	  CPL_ODBC="Deny Access to ODBC"
	  CPL_Ports="Deny Access to Ports"
	  CPL_Server="Deny Access to Server"
	  CPL_System="Deny Access to System"
	  CPL_Telephony="Deny Access to Telephony"
	  CPL_TimeDate="Deny Access to Date/Time"
	  CPL_UPS="Deny Access to UPS"
	  CPL_Hide ="No"
	  CPL_HARDWARE="Deny Access to Hardware Wizard"
	  CPL_MAIL="Deny Access to Mail"
	  CPL_SCANNER="Deny Access to Scanners & Cameras"
	  CPL_POWER="Deny Access to Power Options"
	
	3. Click File, click Save As, type "Cpanel.adm" (without the quotation marks),
	  and then click Save.
	
	To enable the policy:
	
	1. Copy the Cpanel.adm file to the %<SystemRoot>%\Inf folder.
	
	2. Click Start, click Run, type "POLEDIT" (without the quotation marks), and
	  then click OK. Click Options, click Policy Template, click to select the
	  Cpanel.adm file, and then click OK.
	
	3. Click File, click New Policy, and then double-click the icon representing the
	  user name for which you want to prevent the icon display.
	
	4. Double-click Control Panel Icons, click to select the check box for the
	  individual icon entries to prevent their on-screen display, and then click
	  OK.
	
	5. Click File, click Save, type a name for the new policy, and then click Save.
	
	NOTE: If in a Windows NT 4.0 domain you start a Terminal Services session to a
	Windows 2000 Terminal Services server and you have Control Panel disabled or
	Control Panel Printers disabled per this article and you click Print on the File
	menu, you receive the following error message: "Error occured during this
	operation." Clicking the Print icon does not cause this error message. The error
	message occurs because clicking Print on the File menu uses the Control Panel
	printer properties to create the print job; locking Control Panel causes the
	function not to work. This behavior is by design.
	
	For additional information about how to implement the security policy using the
	newly created file, please see the following article in the Microsoft Knowledge
	Base:
	
	  Q168579 How to Set Up Locally-Based System Policies
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbEnableMove kbEnableLearn 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
