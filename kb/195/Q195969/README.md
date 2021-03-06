---
layout: page
title: "Q195969: XFOR:Cannot Specify Domains to Relay to in Internet Mail Service"
permalink: /kb/195/Q195969/
---

## Q195969: XFOR:Cannot Specify Domains to Relay to in Internet Mail Service

{% raw %}

	Article: Q195969
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): kbFEA exc55sp2fea
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When the Exchange Server Internet Mail Service is configured to allow message
	routing (relaying), there is no way to specify what domains are allowed or not
	allowed to be relayed to.
	
	RESOLUTION
	==========
	
	New functionality has been added to the Exchange Server Internet Mail Service to
	allow you to override any previous relay restrictions and specify that mail
	destined for a certain domain be relayed.
	
	To obtain this feature, obtain the latest service pack for Exchange Server
	version 5.5. For more information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The English version of this feature should have the following file attributes or
	later:
	
	  Component: Internet Mail Service
	
	  File Name      Version
	  -------------------------
	  Imcadmin.dll   5.5.2424.0
	  Msexcimc.exe   5.5.2424.0
	
	This feature was first included in Exchange Server 5.5 Service Pack 2.
	
	
	MORE INFORMATION
	================
	
	Installation
	------------
	
	The Imcadmin.dll file requires a special installation process. This file must be
	copied to the Exchsrvr\Add-ins\Smtp\I386 directory and you must also perform the
	following steps:
	
	WARNING: Using the raw mode of the Exchange Server Administrator program (admin
	/r) incorrectly can cause serious problems that may require you to reinstall
	Microsoft Windows NT Server and/or Microsoft Exchange Server. Microsoft cannot
	guarantee that problems resulting from the incorrect use of raw mode can be
	solved. Use raw mode at you own risk.
	
	1. Start the Microsoft Exchange Server Administrator program in raw mode by
	  typing the following at an MS-DOS command-line prompt:
	
	  admin /r
	
	2. Click Site, click Configuration, click the Add-Ins container, and select the
	  Internet Mail Service for <platform>.
	
	3. On the File menu, click Raw Properties, and select File-Version from the
	  Object attributes list.
	
	4. Click Editor, and then double-click File version.
	
	5. Type the proper version as shown above, and then click OK.
	
	6. Click Set to save the changes, and then click OK.
	
	To implement this feature, perform the following steps:
	
	1. In the left pane of the Administrator window, click the Connections object
	  under the appropriate site. In the right pane, click the Internet Mail
	  Service, and then click Properties on the File menu. Note that the
	  Connections object appears under the Configuration object.
	
	2. Click the Routing tab, and then click >Add< to add a domain to which
	  you want to allow routing.
	
	3. In the Edit Routing Table Entry dialog box, type the domain to which you want
	  to allow routing in the "E-Mail Sent to This Domain" box, select the radio
	  button next to 'Override Relay Restrictions. Always "relay"', and then click
	  OK.
	
	4. Click >Routing Restrictions<. If you have not already specified
	  restrictions in the Routing Restrictions dialog box, click the "Hosts and
	  clients with these IP addresses" check box to select it.
	
	  *NOTE: Step 4. is important because without specifying any restrictions, any
	  host or client and relay mail anywhere.
	
	5. Click >OK<, and then click >OK< again.
	
	6. Restart you Microsoft Exchange Internet Mail Service.
	
	Example scenario:
	
	Your domain is A.COM but you are responsible for relaying messages to B.COM and
	C.COM. You want to allow rerouting to B.COM and C.COM but not allow mail
	destined for any other domains to relay.
	
	To do this, use step 2-3 in the implementation section above to create an entry
	for both B.COM and C.COM.
	
	When a host sends a RCPT TO: destined for A.COM, B.COM, and C.COM, the mail will
	now be accepted. But, if a message is TO: any other domain, the host will get a
	"550 Relaying is Prohibited" and the Internet Mail Service will not accept the
	message for delivery.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbFEA exc55sp2fea 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
