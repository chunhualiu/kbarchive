---
layout: page
title: "Q163241: LPR Printers Show Status Unknown"
permalink: /kb/163/Q163241/
---

## Q163241: LPR Printers Show Status Unknown

{% raw %}

	Article: Q163241
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbprint
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	Registry" Help topic in Regedit.exe or the "Restoring a Registry Key" Help
	topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	When you print to a printer through a line printer remote (LPR), the status of
	the printer may show "Status Unknown" in Windows NT 3.51.
	
	When the printer is opened from the Printers folder in Windows NT 4.0, the
	printer may show <Failed to open, Retrying> and the Properties for that
	printer may be unavailable.
	
	If you attempt to add an LPR port, which does not appear in the list of ports but
	actually exists in the registry, the follow error may occur:
	
	  The port already exists.
	
	Additionally, all available LPR ports may not be listed from within Printer
	Properties Details or Ports tabs.
	
	CAUSE
	=====
	
	There are two known possible causes for these symptoms:
	
	- An invalid LPR Port registry entry.
	
	  An invalid registry entry could be caused by manually adding an LPR port with
	  Registry Editor. If the manually added port is missing values, it can cause
	  the above error. It is recommended that an LPR port only be added through the
	  user interface through the Print Manager Printers folder.
	
	- The "\" character was used in the LPD queue name.
	
	  If the "\" character is used anywhere in the line printer daemon (LPD) queue
	  name (name of printer on that machine providing LPD), an additional subkey is
	  added under the name of that port in the registry. This precludes Print
	  Manager or Printers folder from successfully parsing any ports listed below
	  the port with the invalid character in the name.
	
	
	RESOLUTION
	==========
	
	To fix the problem, the invalid port must be removed from the registry. To do
	this, use the following steps:
	
	1. Click the Start button, point to Settings, click Control Panel, and then
	  double-click the Services icon.
	
	2. Select Spooler from the list of services, then click Stop.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	1. Run Registry Editor (Regedt32.exe) and locate the following key:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Monitors
	  \LPR Port\Ports
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	2. Locate any ports with a "\" character in the name or ports that are missing
	  entries. In the most obvious case, the IP port will not have any values or
	  will only have values that were added manually.
	
	  NOTE: Normally the LPR port will have a name that is either the IP address or
	  the DNS name of the destination host providing LPD service
	
	3. With the invalid port selected, click the Edit menu, then click Delete.
	
	4. Quit Registry Editor.
	
	5. Click the Start button, point to settings, click Control Panel, and then
	  double-click the Services icon.
	
	6. Select Spooler from the Services list, and then click Restart.
	
	MORE INFORMATION
	================
	
	Windows NT supports TCP/IP printing as documented in RFC 1179. During the
	creation of an LPR port, an IP address (name or address of host providing lpd:)
	and LPD queue name (name of printer on that machine:) must be provided for the
	print destination.
	
	The following are examples of valid and invalid LPR Port entries:
	
	Valid LPR Port:
	
	HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Print\Monitors
	\LPR Port\Ports\157.61.221.159:Text1\Timeouts
	
	Invalid LPR Port:
	
	HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Print\Monitors
	\LPR Port\Ports\157.61.221.159\<additional_name>\Timeouts
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51 and 4.0.
	We are researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	Additional query words: PrintMan missing port
	
	======================================================================
	Keywords          : kbprint 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : WinNT:3.5,3.51,4.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
