---
layout: page
title: "Q275227: XADM: Error Message: &quot;Unable to Expand the Folder&quot;"
permalink: /kb/275/Q275227/
---

## Q275227: XADM: Error Message: &quot;Unable to Expand the Folder&quot;

{% raw %}

	Article: Q275227
	Product(s): Microsoft Exchange
	Version(s): 
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 26-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange 2000 Server 
	- Microsoft Outlook 2000 
	- Microsoft Outlook 2000, Service Release 1 (SR-1) 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Users cannot log on to their Exchange 2000 mailbox with Outlook 2000 for the
	first time. Actually, Outlook starts without error, and users can see default
	folders, but when they attempt to open one of the folders, they receive the
	following error message:
	
	  Unable to expand the folder. The set of folders could not be opened. The
	  attempt to log on to the Microsoft Exchange Server computer has failed.
	
	In the Application event log, there are events which suggest a successful logon,
	but there is also the following event:
	
	  Event ID: 9562
	  Source: MSExchangeIS
	  Description: Failed to read attribute msExchUSRAccountControl from active
	  directory for /o=Org/ou=Administrative Group/cn=Recipient
	  Container/cn=Mailbox.
	
	CAUSE
	=====
	
	The schema for Exchange 2000 was not properly extended when you upgraded from
	Release Candidate 2 (RC2) to the Release to Manufacturing (RTM) version.
	Specifically, you did not re-run forestprep with the RTM version of Exchange
	2000 Setup. As a result, the msExchUSRAccountControl attribute was not added to
	the schema. This is a required attribute that was added post-RC2.
	
	RESOLUTION
	==========
	
	After you run /forestprep, which forces replication to the child domain, run
	/domainprep in the child domain, and rebuild the Recipient Update Service
	objects. Then you can log on to your mailboxes.
	
	For additional information about how to properly upgrade from Exchange 2000
	Server RC2 to RTM, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q272082 XADM: How to Upgrade from Exchange 2000 RC2 to RTM
	
	
	Additional query words: rus ad exch2kp2w
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbOutlookSearch kbExchangeSearch kbOutlook2000Search kbExchange2000Search kbZNotKeyword3 kbOutlook2000SR1 kbExchange2000Serv
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
