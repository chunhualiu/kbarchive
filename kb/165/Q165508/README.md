---
layout: page
title: "Q165508: SMS: PCM Does Not Follow Correct Distribution Server Logic"
permalink: /kb/165/Q165508/
---

## Q165508: SMS: PCM Does Not Follow Correct Distribution Server Logic

{% raw %}

	Article: Q165508
	Product(s): Microsoft Systems Management Server
	Version(s): 1.0,1.1,1.2,1.2 SP1
	Operating System(s): 
	Keyword(s): kbnetwork kbPCM smspcmkbfixlist
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2, 1.2 SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The 32-bit versions of Package Command Manager (Pcmwin32.exe and Pcmsvc32.exe)
	do not correctly follow the distribution selection logic as described below.
	
	Package Command Manager (PCM) Distribution Server Selection Logic:
	
	1. Check the distribution server list for the package to see if the current
	  logon server exists in the list. If it does exist, then use that server as
	  the distribution server.
	
	2. Check the server names for each currently connected drive letter. If any of
	  the server names for the currently connected drives match a server in the
	  package distribution list, then use that server as the distribution server.
	
	3. Check the current logon server for the package, using the explicit path to
	  the package share. This is to ensure that the current logon server does
	  actually contain the package, even if it is not in the list of 10 package
	  servers.
	
	4. If steps 1-3 fail, randomly select a server from the package distribution
	  list, and connect to that server. If the connection fails for any reason,
	  randomly pick another server from the package server list, until either a
	  server is connected, or the list is exhausted.
	
	CAUSE
	=====
	
	Up to and including Systems Management Server 1.2 Service Pack 1, the 32-bit
	implementation of Package Command Manager did not successfully find a match for
	steps 1-3 indicated above.
	
	
	
	
	
	
	
	Because steps 1 through 3 fail to return a match, the 32-bit implementation of
	Package Command Manager randomly chooses a distribution server from those listed
	in the PCM instruction.
	
	STATUS
	------
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	versions 1.0, 1.1, 1.2, and 1.2 Service Pack 1. This problem was corrected in
	the latest Microsoft Systems Management Server version 1.2 U.S. Service Pack.
	For information on obtaining the service pack, query on the following word in
	the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	----------------
	
	For additional information about PCM, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q180151 SMS: How to Select the PCM Distribution Server Selection Logic
	
	Additional query words: prodsms SP1 distribution package pcm
	
	======================================================================
	Keywords          : kbnetwork kbPCM smspcm kbfixlist
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120 kbSMS120SP1
	Version           : :1.0,1.1,1.2,1.2 SP1
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
