---
layout: page
title: "Q87667: Network Comm. Across Router Using PC-TCP and LAN Manager"
permalink: /kb/087/Q87667/
---

## Q87667: Network Comm. Across Router Using PC-TCP and LAN Manager

{% raw %}

	Article: Q87667
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	SYMPTOMS
	========
	
	When FTP Software's PC-TCP stack is used with Microsoft LAN Manager, the network
	traffic will not go across a router.
	
	Net Sends, Net Views, and Net Uses to workstations across the router will not
	work.
	
	CAUSE
	=====
	
	The NetBIOS uses broadcasts for name claims, name resolution, and nondirected
	datagrams. The RFCs 1001 and 1002 define three ways in which broadcast traffic
	can be handled by a NetBIOS over TCP/IP implementation. These are B-Node
	(Broadcast), P-Node (Point-to- Point), and M-Node (Mixed). B-Node uses
	broadcasts for name contention and resolution. B-Node broadcasts for name
	contention and name resolution do not go through a router. A router will not
	allow a broadcast message to pass through to other networks.
	
	FTP Software's implementation of NetBIOS over TCP/IP is purely B-Node based.
	Therefore, the B-node broadcasts will not go across a router and network
	communications will not take place across the router.
	
	On the other hand, Microsoft's implementation of NetBIOS is also B-node based.
	However, the MS TCP/IP stack uses the LMHOSTS file in LAN Manager to provide the
	NetBIOS-name-to-IP-address mapping. The LMHOSTS file is located in the
	<LANROOT>\ETC directory. By entering the NetBIOS name to IP address
	mapping in the LMHOSTS file, the RFC NetBIOS name query request frames for those
	names will not be sent to the local network. Instead, the cache containing the
	entries in LMHOSTS file will be used to resolve the NetBIOS-name-to-IP-address
	mapping. Therefore, broadcasts will not be generated and the machines will be
	able to communicate across a router.
	
	RESOLUTION
	==========
	
	FTP Software is aware of this situation and according to their technical support
	department the new release of the software (version 2.1) will have a feature
	similar to Microsoft's implementation. The new release is scheduled to come out
	in summer of 1992. For now, the workaround is either to use Microsoft's TCP/IP
	stack or to configure the router to bridge the network traffic.
	
	Reference(s):
	
	For more information regarding B-Node, P-Node, and M-Node communications, please
	refer to RFCs 1001, 1002, TCP/IP technical notes written by Margaret Johnson, or
	the April 1992 issue of "NetNews."
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	

{% endraw %}
