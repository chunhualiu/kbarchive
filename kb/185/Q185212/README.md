---
layout: page
title: "Q185212: Cluster Server Does Not Support More than 900 Shares"
permalink: /kb/185/Q185212/
---

## Q185212: Cluster Server Does Not Support More than 900 Shares

{% raw %}

	Article: Q185212
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbWinNT400sp4fix
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft Cluster Server 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After creating more than 900 total resources on Microsoft Cluster Server on
	Windows NT Server, Enterprise Edition, version 4.0 with Service Pack 3, you may
	receive various RPC errors and observe the following events in the System event
	log:
	
	  1016 (source CLUSSVC)
	  1065 (source CLUCSSVC)
	  1000 (source CLUSSVC)
	  1069 (source CLUSSVC)
	
	CAUSE
	=====
	
	The original release of Cluster Server with Windows NT 4.0 Service Pack 3 does
	not support more than 900 resources. These may be any combination of total
	resources.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT version 4.0 and
	Microsoft Cluster Server. This problem was first corrected in Windows NT 4.0
	Service Pack 4.
	
	
	MORE INFORMATION
	================
	
	In Service Pack 4 and later, the limit is 1,600 resources. To simplify
	administration and reduce overhead, use the "share subdirectories" option
	provided with the file share resource included in Service Pack 4 and later
	service packs. This option allows you to create a single file share resource for
	an unlimited number of shares. Set permissions accordingly at the file system
	level to protect access to the data to be shared.
	
	The "share subdirectories" option for the file share resource was originally
	provided in Service Pack 4 but did not dynamically discover new subdirectories
	added while online. Service Pack 5 contains an update to this feature, allowing
	new subdirectories to be shared automatically. For additional information, see
	the following article in the Microsoft Knowledge Base:
	
	  Q194831 SP4 Cluster Shares Must Be Reset to Recognize Added Subdirectories
	
	The Cluster Service under Windows 2000 Advanced Server and Datacenter Server
	contains the same dynamic support for file shares through the "share
	subdirectories" option.
	
	
	Additional query words: 4.00 mscs shares
	
	======================================================================
	Keywords          : kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbNTTermServ400 kbNTTermServSearch kbAudDeveloper kbClustServSearch
	Version           : :4.0
	Issue type        : kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
