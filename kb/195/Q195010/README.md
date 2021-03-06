---
layout: page
title: "Q195010: Activate_session/Deactivate_session Unavailable in SNA Server"
permalink: /kb/195/Q195010/
---

## Q195010: Activate_session/Deactivate_session Unavailable in SNA Server

{% raw %}

	Article: Q195010
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, 2.11 SP2, 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0, 4.0 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The following APPC verbs are not available for use with SNA Server:
	
	- Activate_session
	
	- Deactivate_session
	
	Please refer to the APPC Programmer's Guide included with the SNA Server Software
	Development Kit for information on the APPC verbs supported by SNA Server.
	
	CAUSE
	=====
	
	The APPC Library included with SNA Server was not written to include support for
	these two APPC verbs.
	
	RESOLUTION
	==========
	
	Microsoft has confirmed this to be a problem in SNA Server versions 2.11, 2.11
	SP1, 2.11 SP2, 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0, and 4.0 SP1. We are
	researching this problem in SNA Server versions 2.11 and 3.0 and will post more
	information here in the Knowledge Base as it becomes available.
	
	This problem was corrected in the latest Microsoft SNA Server version 4.0 U.S.
	Service Pack. For information on obtaining this Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	MORE INFORMATION
	================
	
	This update adds support for the ACTIVATE_SESSION and DEACTIVATE_SESSION APPC
	verbs to the SNA Server's 32-bit APPC library. Therefore, these verbs are
	supported on SNA Server systems, SNA Server Client for Windows NT systems, and
	SNA Server Client for Windows 9x systems.
	
	ACTIVATE_SESSION: Requests SNA Server to activate a session between the Local
	APPC LU and a specified Partner APPC LU, using a specified APPC Mode. This verb
	completes either when the specified session has become active or when it has
	failed.
	
	DEACTIVATE_SESSION: Requests SNA Server to deactivate a particular APPC session
	or all APPC sessions on a particular APPC Mode.
	
	Please refer to the updated APPC Programmer's Guide in the SNA Server SDK for
	complete details on these verbs.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ211 kbSNAServ400 kbSNAServ211SP1 kbSNAServ211SP2 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ300SP2
	Version           : WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0,4.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
