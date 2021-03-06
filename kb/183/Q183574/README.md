---
layout: page
title: "Q183574: Off-line Demo Script Fails in Non-US Locales"
permalink: /kb/183/Q183574/
---

## Q183574: Off-line Demo Script Fails in Non-US Locales

{% raw %}

	Article: Q183574
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:1.0,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 21-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft OLE DB Provider for AS/400 and VSAM, version 1.0, used with:
	   - Microsoft SNA Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	No data is displayed when the off-line demo script is used in non-US locales.
	
	CAUSE
	=====
	
	The problem is due to the CCSID for the fields, which is 937.
	
	The varchar fields in this file are incorrectly set up as CCSID 937 (Traditional
	Chinese). If you have installed the EBCDIC NLS files for 937, then SNAOLEDB
	attempts to convert the data.
	
	The data is actually U.S. English upper-case and lower-case characters, which do
	not map well when converted from 937 to PC code page 950. The result shows
	blanks when viewed via the OLE DB provider.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft OLE DB Provider for
	AS/400 and VSAM version 1.00, included with Microsoft SNA Server version 4.0.
	
	This problem was corrected in the latest SNA Server version 4.0 U.S. Service
	Pack. For information on obtaining this Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbOLEDBSearch kbOLEDBProvSearch
	Version           : WINDOWS:1.0,4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
