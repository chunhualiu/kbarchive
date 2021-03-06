---
layout: page
title: "Q182266: SNA APPC Event 93 Should Log Fully Qualified PLU Name"
permalink: /kb/182/Q182266/
---

## Q182266: SNA APPC Event 93 Should Log Fully Qualified PLU Name

{% raw %}

	Article: Q182266
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 14-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If a CPIC or APPC application attempts to allocate a conversation and specifies
	a fully qualified Primary (that is, Remote) APPC LU name (instead of the Remote
	LU alias), and the allocation attempt fails, the SNA Server APPC interface logs
	Event 93, but does not indicate the fully qualified PLU name in the event. For
	example:
	
	  Event ID: 93
	  Source:   SNA APPC Application
	  Description:
	  APPC local conversation start failed:
	  Primary_rc   = <Return code>
	  Secondary_rc = <Return code>
	  TP_ID        = <Transaction program ID>
	  Dest TP name = <Destination TP name>
	  LU alias     = <Local APPC LU alias>
	  PLU alias    = <Remote APPC LU alias>
	  Mode name    = <APPC mode name>
	
	  EXPLANATION%
	  An attempt to start an APPC conversation locally using the verb
	  [MC_]ALLOCATE failed.
	
	CAUSE
	=====
	
	The SNA Server Event 93 was not originally designed to log the fully qualified
	PLU name.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server 3.0, 3.0 Service Pack
	1 (SP1), 3.0 SP2, and 4.0. This problem was corrected in the latest SNA Server
	version 3.0 and 4.0 U.S. Service Packs. For information on obtaining this
	Service Pack, query on the following word in the Microsoft Knowledge Base
	(without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	With this update applied, the SNA Server APPC DLL (Wappc32.dll) logs the fully
	qualified PLU name, in addition to the other fields noted above.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2,4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
