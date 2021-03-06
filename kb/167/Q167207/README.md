---
layout: page
title: "Q167207: XADM: Incorrect Status for Storage Limits in Mailbox Resources"
permalink: /kb/167/Q167207/
---

## Q167207: XADM: Incorrect Status for Storage Limits in Mailbox Resources

{% raw %}

	Article: Q167207
	Product(s): Microsoft Exchange
	Version(s): WinNT: 4.0, 5.0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 24-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If you add the Storage Limits column to Mailbox Resources in the properties for
	the Private Information Store, the status of the mailboxes that reach the
	Prohibit Send limit is reported incorrectly.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 4.0. We are researching this problem and will post new information here
	in the Microsoft Knowledge Base as it becomes available.
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server version
	5.0. This problem has been corrected in the latest U.S. Service Pack for
	Microsoft Exchange Server version 5.0. For information on obtaining the service
	pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	On the General tab for the Private Information Store Properties you can choose
	to set an Issue Warning limit and a Prohibit Send limit. On the Mailbox
	Resources tab you can click the Columns button and add the Storage Limits
	column. This column reports a status, depending on the amount of storage space
	used by each mailbox. These are:
	
	- Below Limit: The mailbox is below the Issue Warning limit indicated on the
	  General tab of the Private Information Store Properties.
	
	- Issue Warning: The mailbox has reached or surpassed the Issue Warning limit,
	  but is lower than the Prohibit Send limit.
	
	- Prohibit Send: The mailbox has reached or surpassed the Prohibit Send limit.
	
	- No Checking: There are no limits set on the General tab of the Private
	  Information Store Properties.
	
	If you add the Storage Limits column to Mailbox Resources, the Prohibit Send
	status will not show until the mailbox has reached the Issue Warning limit plus
	the Prohibit Send limit. For example, if you set an Issue Warning limit of 5000K
	and a Prohibit Send limit of 7000K, then the Prohibit Send status will not show
	in the Storage Limits column until the mailbox reaches 12000K in size.
	
	The Issue Warning status works correctly, and any mailbox that reaches the
	Prohibit Send limit is prevented from sending any messages. This is only a
	status reporting problem.
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbZNotKeyword2
	Version           : WinNT: 4.0, 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
