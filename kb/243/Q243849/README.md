---
layout: page
title: "Q243849: Nslookup &quot;ls&quot; Command Generates &quot;&#42;&#42;&#42;Can't List Domain&quot; Error"
permalink: /kb/243/Q243849/
---

## Q243849: Nslookup &quot;ls&quot; Command Generates &quot;&#42;&#42;&#42;Can't List Domain&quot; Error

{% raw %}

	Article: Q243849
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kberrmsg kbtool kbWinNT400PreSP7Fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the "ls" command with the Nslookup tool, you may receive the
	following error message:
	
	  ***Can't list domain <name>: Query refused
	
	WORKAROUND
	==========
	
	To work around this problem, type the TCP/IP address of the local Domain Name
	System (DNS) server in the notify list. The Nslookup "ls" command then runs
	successfully. However, DNS logs warning event 7062 once in the Event log:
	
	  DNS Server encountered a packet addressed to itself -- IP address
	  <w.x.y.z>.
	  The DNS server should never be sending a packet to itself. This situation
	  usually indicates a configuration error.
	
	For additional information, click the article number below to view the article in
	the Microsoft Knowledge Base:
	
	  Q218814 DNS Server Logs Event 7062: 'DNS Server Encountered a Packet...'
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Apply it only to systems
	that are experiencing this specific problem.
	
	To resolve this problem, contact Microsoft Product Support Services to obtain the
	fix. For a complete list of Microsoft Product Support Services phone numbers and
	information about support costs, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English-language version of this fix should have the following file
	attributes or later:
	
	  Date      Time    Version      Size    File name     Platform
	  -------------------------------------------------------------
	  11/05/99  04:42p               178,448 Dns.exe       x86
	  11/05/99  04:41p               299,280 Dns.exe       Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	The error message described above occurs under the following circumstances:
	
	- You run the Nslookup "ls" command locally on your DNS server to list a local
	  domain.
	
	- The "Only Allow Access from Secondaries Included on Notify List" option is
	  enabled on your DNS server's zone, and the DNS server's local TCP/IP address
	  is not entered in the notify list.
	
	In this case, DNS assumes that a query of a non-authorized DNS server is received
	and the error message is returned.
	
	The hotfix allows the Nslookup "ls" command to return successfully without adding
	the local TCP/IP address to the notify list. However, the following messages are
	logged in the Event log:
	
	  6000 (Informational) DNS_EVENT_ZONEXFR_START
	  DNS Server initiating transfer of zone %1 to DNS server at %2.
	
	  6001 (Informational) DNS_EVENT_ZONEXFR_SUCCESSFUL
	  DNS Server transfer of zone %1 to DNS server at %2, successfully completed.
	
	NOTE: If you use the hotfix and unnecessarily add the local TCP/IP address to the
	DNS server's notify list, warning 7062 is still logged in the Event log once for
	every zone to which this applies. When you restart the DNS server, you also
	receive the warning once for every zone that has the server's local address in
	its notify list.
	
	Additional query words:
	
	======================================================================
	Keywords          : kberrmsg kbtool kbWinNT400PreSP7Fix 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400
	Version           : winnt:4.0
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
