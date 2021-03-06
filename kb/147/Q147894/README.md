---
layout: page
title: "Q147894: BUG: Spy++ Causes Exception in Owner-Drawn Combo Box"
permalink: /kb/147/Q147894/
---

## Q147894: BUG: Spy++ Causes Exception in Owner-Drawn Combo Box

{% raw %}

	Article: Q147894
	Product(s): Microsoft C Compiler
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Using Spy++ with message logging on an owner-drawn combo box results in one of
	the following errors:
	
	  First-chance exception in OWNCOMBO.exe (USER32.DLL): 0xC0000005: Access
	  Violation.
	
	  -or-
	
	  First-chance exception in OWNCOMBO.exe (KERNEL32.DLL): 0xC0000005: Access
	  Violation.
	
	This exception is printed out in the Visual C++ debug output window. This happens
	both on Windows 95 and Windows NT version 3.51.
	
	RESOLUTION
	==========
	
	This exception is caused by the Spy++ installed Windows hook function. It
	doesn't cause the program to quit, so no action should be necessary.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	In the sample used to produce this error, the owner-drawn combo box did not have
	the style CBS_HASSTRINGS. A 32-bit value was being passed to the combo box by
	way of CB_ADDSTRING. This appears to cause the exception when the Spy++ message
	logging is turned on.
	
	This error did not occur in previous versions of Spy++.
	
	Steps to Reproduce Error
	------------------------
	
	1. Load the project of the OWNCOMBO sample as provided with Visual C++ 4.0.
	
	2. On the Build menu, click Rebuild All to get a debug executable.
	
	3. Start Owncombo.exe by pressing F5.
	
	4. On the View menu, click Output in Visual C++ 4.0.
	
	5. Start Spy++ and move its window as well as OWNCOMBO's window so that MSDEV's
	  output window is visible.
	
	6. In OWNCOMBO, on the Examples menu, click Owner Draw Combo Box.
	
	7. In Spy++, on the Spy menu, click Find Window.
	
	8. Use the Finder Tool, and drag it over the combo box in OWNCOMBO.
	
	9. In Spy++, under Show, click Messages, and then click OK.
	
	10. In OWNCOMBO, add a color to the combo box (either Red or Blue).
	
	Additional query words: kbVC400bug 4.00 4.10 4.20
	
	======================================================================
	Keywords          :  
	Technology        : kbVCsearch kbAudDeveloper kbVC600 kbVC32bitSearch
	Version           : :6.0
	
	=============================================================================
	

{% endraw %}
