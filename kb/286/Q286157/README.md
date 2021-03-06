---
layout: page
title: "Q286157: Blank Page May Be Printed at the Start of Host Print Jobs"
permalink: /kb/286/Q286157/
---

## Q286157: Blank Page May Be Printed at the Start of Host Print Jobs

{% raw %}

	Article: Q286157
	Product(s): Microsoft SNA Server
	Version(s): 4.0 SP3,4.0 SP4
	Operating System(s): 
	Keyword(s): kbDSupport kbsna400sp3 kbhis2000 kbsna400sp4
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 4.0 SP3, 4.0 SP4 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Host print jobs may print an extra blank page at the beginning of the print job
	after you apply SNA Server 4.0 Service Pack 3 (SP3) or SP4. In addition, the
	same symptoms may occur when you upgrade from SNA Server 4.0 SP2 or earlier to
	Host Integration Server 2000.
	
	The blank page is printed when the host print job includes a Form Feed (0x0C) at
	the beginning of the print job, even though the FEEDIGNOREINITIAL option is
	configured for the LU3 print session.
	
	The problem does not occur with SNA Server 3.0 SP4, SNA Server 4.0 SP1, or SNA
	Server 4.0 SP2 when you print the same LU3 print job when the FEEDIGNOREINITIAL
	option is configured.
	
	Note This problem can occur with both LU1 and LU3 print jobs.
	
	CAUSE
	=====
	
	The FEEDIGNOREINITIAL parameter is not checked because of a change that was made
	to the host print service in SNA Server 4.0 SP3.
	
	
	RESOLUTION
	==========
	
	SNA Server 4.0:
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft SNA Server 4.0 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	+------------------------------------+
	| File name   | Date       | Time    | 
	+------------------------------------+
	| Winvprt.dll | 01/31/2001 | 06:46AM | 
	+------------------------------------+
	
	NOTE: Because of file dependencies, the most recent fix that contains the above
	files may also contain additional files.
	
	
	
	Host Integration Server 2000:
	
	See the following Microsoft Knowledge Base article for the Host Integration
	Server 2000 resolution to this problem:
	
	  Q289658 FeedIgnoreInitial Not Always Honored on HIS 2000 Print Sessions
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft SNA Server versions
	4.0 SP3 and SP4, and Host Integration Server 2000.
	
	MORE INFORMATION
	================
	
	For additional information about the FEEIGNOREINITIAL configuration option,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q185676 FEEDIGNOREINITIAL Option Not Working in Snaprint
	
	Additional query words: extra page
	
	======================================================================
	Keywords          : kbDSupport kbsna400sp3 kbhis2000 kbsna400sp4 
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400SP3 kbSNAServ400SP4
	Version           : :4.0 SP3,4.0 SP4
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
