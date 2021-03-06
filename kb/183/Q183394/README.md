---
layout: page
title: "Q183394: XADM: Event Agent Fires Every 15 min If No Schedule Is Defined"
permalink: /kb/183/Q183394/
---

## Q183394: XADM: Event Agent Fires Every 15 min If No Schedule Is Defined

{% raw %}

	Article: Q183394
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55
	Last Modified: 24-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5, on platform(s):
	   - the hardware: DEC Alpha 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When installing an Event Agent to a folder in Exchange 5.5, the user can select
	the "A scheduled event occurs" event handler. If the user does not click
	Schedule and define a specific schedule, the Event will fire on a 15 minute
	interval, however, the expected behavior is that this event would not fire at
	all.
	
	When the user checks the Scheduled Event properties page, the Schedule is set to
	Hourly, with the Run Event set for Every 0 hour and 0 min.
	
	WORKAROUND
	==========
	
	Explicitly click Schedule and define a specific schedule.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Exchange Server 5.5 for Alpha.
	We are researching this problem and will post new information here in the
	Microsoft Knowledge Base as it becomes available.
	
	Additional query words: Server Side Scripting Service
	
	======================================================================
	Keywords          : exc55 
	Technology        : kbExchangeSearch kbZNotKeyword2
	Version           : winnt:5.5
	Hardware          : ALPHA
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
