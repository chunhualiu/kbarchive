---
layout: page
title: "Q277826: Err Msg: The Currently Selected Display Resolution Is Invalid"
permalink: /kb/277/Q277826/
---

## Q277826: Err Msg: The Currently Selected Display Resolution Is Invalid

{% raw %}

	Article: Q277826
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbdisplay kbenv kberrmsg kbhw kbHardware
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	After you install a new video adapter driver, you may receive the following
	error message:
	
	  Invalid Display settings
	  The currently selected display resolution is invalid
	  Please use the display option in the Windows NT Control Panel to select your
	  preferred display resolution.
	
	The video adapter tests correctly at any supported resolution and color depth,
	but the desktop is displayed only with the default VGA colors and resolution.
	
	CAUSE
	=====
	
	The behavior occurs if the Basevideo subkey is present under the following
	registry location:
	
	  HKEY_LOCAL_MACHINE\CurrentControlSet\Control\GraphicsDrivers
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To resolve this issue:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Locate and click the following registry key:
	
	  HKEY_LOCAL_MACHINE\CurrentControlSet\Control\GraphicsDrivers
	
	3. Remove the Basevideo subkey if it exists.
	
	4. Quit Registry Editor and then restart the computer.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbdisplay kbenv kberrmsg kbhw kbHardware 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
