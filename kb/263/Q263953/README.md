---
layout: page
title: "Q263953: &quot;Modify Error 18032&quot; Error When Creating New Management Agent"
permalink: /kb/263/Q263953/
---

## Q263953: &quot;Modify Error 18032&quot; Error When Creating New Management Agent

{% raw %}

	Article: Q263953
	Product(s): Microsoft Windows NT
	Version(s): 2.1
	Operating System(s): 
	Keyword(s): kberrmsg kbsetup
	Last Modified: 02-MAR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Metadirectory Services, version 2.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you install Microsoft Metadirectory Services (MMS) and try to create a new
	management agent, the following error message may be displayed:
	
	  DS Action Modification request returns 32 Modify error 18032 Error setting
	  metaverse location
	
	CAUSE
	=====
	
	This behavior occurs because the MMS server did not initialize during the
	installation process.
	
	RESOLUTION
	==========
	
	To resolve this behavior, use either of the following methods:
	
	- Reinstall MMS from the CD-ROM.
	
	- Re-initialize your existing MMS database by running the following command at
	  a command prompt:
	
	  zoomserv\bin\init\init.bat
	
	WARNING: Running the Zoomserv\Bin\Init\Init.bat file from a command prompt
	re-initializes your database and erases all the contents of the MMS directory
	store.
	For additional information about how to use the Init.bat tool, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q255809 Using the Init.bat Utility in Microsoft Metadirectory Services
	
	  Q279692 Init.bat Does Not Correctly Reinitialize the Database
	
	Additional query words: zoomit via fail fails
	
	======================================================================
	Keywords          : kberrmsg kbsetup 
	Technology        : kbMMSSearch kbMMS210
	Version           : :2.1
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
