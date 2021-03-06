---
layout: page
title: "Q243727: XCLN: DMS Clients Cannot Send Mail to Distribution Lists"
permalink: /kb/243/Q243727/
---

## Q243727: XCLN: DMS Clients Cannot Send Mail to Distribution Lists

{% raw %}

	Article: Q243727
	Product(s): Microsoft Exchange
	Version(s): ; WINDOWS:95,98
	Operating System(s): 
	Keyword(s): 
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Outlook 97, on platform(s):
	   - the operating system: Microsoft Windows 95 
	   - the operating system: Microsoft Windows 98 
	- Microsoft Outlook 98, on platform(s):
	   - the operating system: Microsoft Windows 95 
	   - the operating system: Microsoft Windows 98 
	- Microsoft Outlook 2000, on platform(s):
	   - the operating system: Microsoft Windows 95 
	   - the operating system: Microsoft Windows 98 
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you attempt to send a message to a distribution list (DL) by using a client
	that is Defense Message System (DMS) enabled, you receive the following
	non-delivery report (NDR):
	
	  Your message did not reach some or all of the intended recipients.
	
	  Subject:
	  Sent:
	
	  The following recipient(s) could not be reached:
	
	  "<DL name>" 10/13/99 10:25 AM
	
	  Unable to deliver the message because the originator prohibited the expansion
	  of distribution lists
	
	  The MTS-ID of the original message is: c=US;a= ;p=ORGANIZATION;l="<message
	  ID>"
	
	  MSEXCH:MSExchangeMTA:Server name
	
	Event ID 150 is logged in the application event log of the Microsoft Exchange
	Server computer as follows:
	
	  Event ID 150:
	
	  Source: MSExchangeMTA
	
	  An error occurred while expanding a distribution list. The MTS-ID of the
	  message is <message ID>. The reason code is <error code>.
	
	MORE INFORMATION
	================
	
	By default, the DMS version 2.0 clients are not given the permissions to expand
	DLs, in accordance with DMS specifications.
	
	To change this behavior on a message-by-message basis:
	
	1. Create a new message.
	
	2. On the File menu, click Military Properties.
	
	3. Click the Delivery tab.
	
	4. Click to clear the Prohibit Send to DLs check box.
	
	This functionality is limited to signed and sealed messages only in DMS version
	2.1 and DMS version 2.2 clients.
	
	Additional query words: 8.0 8.01 8.02 8.03 8.04 8.5 9.0
	
	======================================================================
	Keywords          :  
	Technology        : kbOutlookSearch kbOutlook97Search kbZNotKeyword3
	Version           : :; WINDOWS:95,98
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
