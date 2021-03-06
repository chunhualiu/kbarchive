---
layout: page
title: "Q317603: Starting SNA Server Service May Cause Event 630 to Be Logged"
permalink: /kb/317/Q317603/
---

## Q317603: Starting SNA Server Service May Cause Event 630 to Be Logged

{% raw %}

	Article: Q317603
	Product(s): Microsoft SNA Server
	Version(s): 3.0,3.0 SP1,3.0 SP2,3.0 SP3,3.0 SP4,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Operating System(s): 
	Keyword(s): kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 kbsna400sp
	Last Modified: 16-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 3.0 SP4, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you start the SNA Server service (Snaservr.exe), the following warning event
	may be posted in the application log of the Event Viewer:
	
	  Event 630 - Source: SNA Host Security
	
	  RPC Layer returned error 0x5 (Access is denied.) This may happen if host
	  security is not installed or the user account the service is running under is
	  not privileged to send messages to the remote end.
	
	MORE INFORMATION
	================
	
	The SNA Server service initializes the Host Security DLL (Snasii.dll) when the
	service starts. During this process, Snasii.dll attempts to locate a domain
	controller (DC) to find a valid host account cache (HAC) database. This DLL is
	initialized even if Host Security Integration is not installed.
	
	In cases where Host Security is used, this event may be logged if the service
	account under which the SNA Server service is running does not have proper
	rights to access the DC and locate the HAC.
	
	Following is a section of a SNA Server internal trace file (Nodeintx.atf), that
	shows a failure due to security:
	
	  SendLocateMessage GetDomainPdc returned PDC \\<Server_Name>, NT Domain
	
	  SendGenericMessage Opened connection to server type MDB on protocol ncacn_np
	
	  SendGenericMessage About to invoke RPC on binding
	  b1c7c350-c091-11cf-a65e-0020afc28c52@ncacn_np:\\\\<Server_Name>
	
	  SendGenericMessage RPC on binding
	  b1c7c350-c091-11cf-a65e-0020afc28c52@ncacn_np:\\\\<Server_Name>
	  returned error: 0x5 (Access is denied.)
	
	  SendGenericMessage RPC Layer returned error 0x5 (Access is denied.) This may
	  happen if host security is not installed or the user account the service is
	  running under, is not privileged to send messages to the remote end.
	
	  HsLogEvent ERROR CODE 0xA1500276, strings:""
	  HsLogEvent Warning type string
	
	NOTE: Logging this event does not cause any performance concerns or overhead. You
	cannot suppress this event.
	
	REFERENCES
	==========
	
	For additional information about causes for an Event 630, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q216558 Recycling Server Causes Invalid RPC Binding for Host Security
	
	  Q248354 Changing Password on Host Security Service Account Causes SSO to Fail
	
	For additional information about Snasii.dll, see the following article in the
	Microsoft Knowledge Base:
	
	  Q265384 Snasii.dll Always Tries to Locate Host Account Cache Database
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 kbsna400sp4 _IK954 Kbhostintegserv2000 
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ300 kbSNAServ400 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3 kbSNAServ400SP4 kbSNAServ300SP2 kbSNAServ300SP4
	Version           : :3.0,3.0 SP1,3.0 SP2,3.0 SP3,3.0 SP4,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
