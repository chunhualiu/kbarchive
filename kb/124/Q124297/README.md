---
layout: page
title: "Q124297: SMS Doc Err: Package Rule Filename Incorrect"
permalink: /kb/124/Q124297/
---

## Q124297: SMS Doc Err: Package Rule Filename Incorrect

{% raw %}

	Article: Q124297
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0
	Operating System(s): 
	Keyword(s): kbdocerr kbAudit smsaudit smsdocerr
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Page 219 of the Microsoft Systems Management Server version 1.0 "Administrator's
	Guide," shows the following syntax for the RUL2CFG.BAT file:
	
	     rul2cfg packagerulefile cfgfile
	
	For the audit process to work correctly, the package rule file output file must
	be named AUDIT.CFG; you cannot use an arbitrary filename.
	
	When the package rule file process completes, AUDIT.CFG is placed in the
	appropriate platform directory. For example, for Intel-based platforms, the file
	is placed in the SMS\PRIMSITE.SRV\AUDIT\PACKAGE\X86.BIN directory. You can test
	this file by running AUDIT32.EXE. If the file is named and compiled correctly,
	you will see the Audit Status count slowly to 100 percent. If the file is
	incorrectly named, the Audit Status immediately displays 100 percent.
	
	Additional query words: sms prodsms
	
	======================================================================
	Keywords          : kbdocerr kbAudit smsaudit smsdocerr 
	Technology        : kbSMSSearch kbSMS100
	Version           : winnt:1.0
	
	=============================================================================
	

{% endraw %}
