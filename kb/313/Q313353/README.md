---
layout: page
title: "Q313353: SMS 2.0 SP3 Is Required to Support Windows XP Clients"
permalink: /kb/313/Q313353/
---

## Q313353: SMS 2.0 SP3 Is Required to Support Windows XP Clients

{% raw %}

	Article: Q313353
	Product(s): Microsoft Systems Management Server
	Version(s): 1.2,2.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 11-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.2, 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Systems Management Server (SMS) 2.0 Service Pack 3 (SP3) is the minimum
	requirement for supporting Microsoft Windows XP Professional-based computers as
	clients.
	
	Not all versions of Windows XP are supported, nor do all versions of SMS support
	Windows XP.
	
	MORE INFORMATION
	================
	
	- Earlier service packs for SMS 2.0, including Service Pack 2 (SP2), do not
	  support Windows XP Professional as a client.
	
	- SMS 1.2 does not support Windows XP as a client.
	
	- No version of SMS supports Microsoft Windows XP Home Edition as a client.
	
	- 64-bit versions of Windows XP are not currently supported as SMS 2.0 clients
	  in either 32-bit or 64-bit mode.
	
	- No version of SMS currently supports Microsoft Windows XP Embedded as a
	  client.
	
	- Additional Quick Fix Engineering (QFE) updates or hotfixes may also be
	  required for Windows XP-based clients.
	
	
	SMS components that are fully supported with no qualifications include:
	
	  Client Installation
	  Hardware Inventory
	  Software Inventory
	  Network Monitor
	
	The following SMS components are supported with some qualifications:
	
	- Software Distribution - When it is initially installed, SP3 Software
	  Distribution cannot target Windows XP-based client computers. This occurs
	  because Windows XP is not recognized by Windows Management Instrumentation
	  (WMI). To add Windows XP to the list of operating systems that SMS uses to
	  target software distribution, install the SP3 hotfix that is described in the
	  following Microsoft Knowledge Base article:
	
	  Q308271 How to Add Windows XP Professional As a Target Platform to SMS 2.0
	  SP3
	
	- Remote Tools - This feature is supported on SMS clients that run Windows XP
	  with a new accelerated video driver. This driver is delivered when the client
	  is upgraded to SP3 or when an SP3 client is initially installed. The Remote
	  Tools feature is supported by using the RLE compression method instead of the
	  default LZH compression method.
	
	
	- Software Metering - There is limited support for software metering of Windows
	  XP. SMS cannot perform software metering of 16-bit programs on a Windows
	  XP-based client.
	
	For additional information about adding Windows XP Professional as an SMS client,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q310614 SMS: The SMS Client Is Not Supported on 64-Bit Versions of Windows XP
	
	For additional information about support for Windows XP, visit the following
	Microsoft Web site:
	
	  http://www.Microsoft.com/smsmgmt/techdetails/newsupport.asp
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbSMSSearch kbSMS120 kbSMS200
	Version           : :1.2,2.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
