---
layout: page
title: "Q185448: Dbview Fails to Display SNA Server 4.0 Message Database"
permalink: /kb/185/Q185448/
---

## Q185448: Dbview Fails to Display SNA Server 4.0 Message Database

{% raw %}

	Article: Q185448
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you install the Dbview utility from the Microsoft SNA Server version 4.0
	CD (by running Dbview.exe from the Docs\Msgdb folder), when you attempt to open
	a message database file (either Snamsg.mdb or Comtimsg.mdb), the following error
	message appears:
	
	  Sorry, this control has expired. Please obtain a newer version.
	
	CAUSE
	=====
	
	The Dbview utility was built with a control that expired in January 1998, which
	causes the failure to occur.
	
	WORKAROUND
	==========
	
	The Dbview utility will work if the local machine date is set to 1997 or
	earlier.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 4.0. This
	problem has been corrected in the latest U.S. Service Pack for SNA Server
	version 4.0. For information on obtaining the Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400
	Version           : WINDOWS:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
