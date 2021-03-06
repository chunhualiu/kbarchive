---
layout: page
title: "Q108738: Browsing Non-Networked Computers Over RAS"
permalink: /kb/108/Q108738/
---

## Q108738: Browsing Non-Networked Computers Over RAS

{% raw %}

	Article: Q108738
	Product(s): Microsoft Windows NT
	Version(s): 2.1,3.1,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.1, 4.0 
	- Microsoft Windows NT Workstation versions 3.1, 4.0 
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft LAN Manager, version 2.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are using Remote Access Service (RAS) to call a computer that is not on
	a network (such as a computer at your home) from a networked computer (such as a
	computer at your office), you are unable to browse the non-networked computer
	for computer names and share names.
	
	CAUSE
	=====
	
	Browsing is automatically disabled in Windows NT if no network other than RAS is
	present. This behavior is based on the assumption that people will only call
	from the non-networked (home) computer to the networked (work) computer, and
	therefore have no need to browse the non-networked (home) computer.
	
	RESOLUTION
	==========
	
	To work around this problem, follow these steps:
	
	1. In Control Panel, double-click Network.
	
	2. On the Services tab, double-click Remote Access Service, click Network, and
	  then click Configure.
	
	3. Click Entire Network, click OK, click OK, and then click Continue.
	
	4. Make sure the non-networked (home) computer is a member of the domain or
	  workgroup of the network where it is called from.
	
	5. In the Network dialog box, click the Adapters tab, click Add, click MS
	  Loopback Adapter, click OK, and then click OK.
	
	  -or-
	
	  Install an additional network card and driver (in addition to RAS).
	
	NOTE: You now have a fake network and options in File Manager and other
	applications appear to be active and functional, but are not functional unless
	you are having a RAS session to another machine.
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTW310 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS310 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS310search kbAudDeveloper kbWinNT310Search kbWinNTW310Search kbLanManSearch kbLanMan210
	Version           : :2.1,3.1,4.0
	
	=============================================================================
	

{% endraw %}
