---
layout: page
title: "Q194620: I_DOTLESS_SMALL in PDF Always Maps to Space"
permalink: /kb/194/Q194620/
---

## Q194620: I_DOTLESS_SMALL in PDF Always Maps to Space

{% raw %}

	Article: Q194620
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:4.0,4.0SP1
	Operating System(s): 
	Keyword(s): kbfixlist
	Last Modified: 20-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0, 4.0SP1 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you attempt to use a Printer Definition File (PDF) to map I_DOTLESS_SMALL
	to an alternate character, the SNA Print service will ignore the mapping and
	always produce a space character represented as 20 in ASCII.
	
	CAUSE
	=====
	
	The SNA Print Service was incorrectly ignoring the I_DOTLESS_SMALL character
	mapping in the PDF.
	
	RESOLUTION
	==========
	
	SNA Server 4.0
	--------------
	
	Microsoft has confirmed this to be a problem in SNA Server version 4.0 and 4.0
	Service Pack 1. This problem was corrected in the latest SNA Server version 4.0
	U.S. Service Pack. For information on obtaining this Service Pack, query on the
	following word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	SNA Server 3.0
	--------------
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	3.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q184307 How to Obtain the Latest SNA Server Version 3.0 Service Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server 3.0 and 4.0. This
	problem was first corrected in SNA Server 3.0 Service Pack 4.
	
	Additional query words:
	
	======================================================================
	Keywords          :  kbfixlist
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ400
	Version           : WINDOWS:4.0,4.0SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
