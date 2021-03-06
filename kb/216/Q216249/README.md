---
layout: page
title: "Q216249: DNS Client Does Not Try All Servers in the DNS Service List"
permalink: /kb/216/Q216249/
---

## Q216249: DNS Client Does Not Try All Servers in the DNS Service List

{% raw %}

	Article: Q216249
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 2,2.1
	Operating System(s): 
	Keyword(s): kbnetwork osr2 win95kbfixlist
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows 95 OEM Service Release, versions 2, 2.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run a DNS query and the query returns an error message (such as "Server
	failure [rcode 2]"), other servers in the list are not queried. The failure is
	passed back to the originator, even though another querying server in the list
	could complete the query.
	
	CAUSE
	=====
	
	Secondary servers are queried only if no response is received from the primary
	server in the server list.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next update that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	  Version    Date              Size           File name
	  -----------------------------------------------------
	  4.10.1660  1/07/99 06:04pm   43,520 bytes   Rnr20.dll 
	
	NOTE: Due to file dependencies, the most recent hotfix or feature that contains
	the above files may also contain additional files.
	
	NOTE: You must install the Winsock 2.0 Update to use this fix. For information
	about obtaining the Winsock 2.0 Update, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q182108 Availability of Windows Sockets 2.0 for Windows 95
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	The DNS query algorithm has been modified to try other servers in the server
	list if an error response is received from a server that could be resolved by
	trying another server in the list. The new algorithm retries servers until:
	
	- The name query is answered successfully
	- An authoritative answer is received from a server that the requested host
	  does not exists (rcode 3)
	- The server list is exhausted
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork osr2 win95 kbfixlist
	Technology        : kbWin95search kbOPKSearch kbZNotKeyword3 kbWin95OPKOSR2 kbWin95OPKOSR210
	Version           : :2,2.1
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
