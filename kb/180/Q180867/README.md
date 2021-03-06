---
layout: page
title: "Q180867: SNA Server Fails to Map Host User ID/Password"
permalink: /kb/180/Q180867/
---

## Q180867: SNA Server Fails to Map Host User ID/Password

{% raw %}

	Article: Q180867
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2
	Operating System(s): 
	Keyword(s): kbfixlist
	Last Modified: 02-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If two SNA subdomains share a common Host Account Cache Master Database (MDB)
	and Backup Host Account Cache within a single Windows NT Domain, single signon
	support may fail.
	
	If the Primary Host Account Cache MBD is unavailable and later becomes available
	for Host User ID or password replacement, that replacement may never occur.
	
	For LU6.2 conversation requests, this could cause a user ID and password of
	MS$SAME to flow in the FMH-5 Attach message. For 3270 signon requests, this
	could cause MS$SAMEU or MS$SAMEP to flow in the host login request.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 3.0, 3.0 SP1,
	and 3.0 SP2.
	
	This problem was corrected in the latest SNA Server version 3.0 U.S. Service
	Pack. For information on obtaining this Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	This problem does not occur in SNA Server 4.0.
	
	To reproduce the problem in SNA Server 3.0, follow these steps:
	
	1. Configure a Host Account Cache on a Windows NT Server Primary Domain
	  Controller. Refer to this computer as PDC1.
	
	2. The Windows NT Server PDC also serves as the Primary SNA Server for SNA
	  Subdomain number 1.
	
	3. Configure a Windows NT Server Backup Domain Controller as a Backup SNA Server
	  for Subdomain 1. Refer to this computer as BDC1.
	
	4. Configure a Backup Host Account Cache on the Backup Domain Controller.
	
	5. Configure a third SNA Server in Subdomain 2. This computer acts as a client
	  to the Host Account Cache. Refer to this computer as BDC2.
	
	6. All SNA Servers and Host Account Cache are in service.
	
	7. Initiate a User ID or password mapping request from BDC2. This computer
	  contacts PDC1. PDC1 directs the request to BDC1. The request is successful.
	
	8. Remove the network cable from PDC1. It is now off the network.
	
	9. Initiate a User ID or password mapping request from BDC2. This computer
	  contacts BDC1 and looks for PDC1. The request fails. This is normal behavior.
	
	10. Replace the network cable on PDC1. It is now on the network.
	
	11. Initiate a User ID or password mapping request from BDC2. This computer
	  contacts BDC1,BDC1 attempts to contact PDC1. The request fails.
	
	Additional query words:
	
	======================================================================
	Keywords          :  kbfixlist
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
