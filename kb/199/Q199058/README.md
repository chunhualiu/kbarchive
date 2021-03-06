---
layout: page
title: "Q199058: BUG: Debugger.SetNextStatement Displays Dialog Box"
permalink: /kb/199/Q199058/
---

## Q199058: BUG: Debugger.SetNextStatement Displays Dialog Box

{% raw %}

	Article: Q199058
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:1.0,1.1,97; winnt:5.0,6.0
	Operating System(s): 
	Keyword(s): kbAutomation kbide kbVC500 kbVC600 kbVCObj kbVisID100 kbVJ100 kbVJ110 kbVS97 kbDevStudi
	Last Modified: 18-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	- Microsoft Visual J++, versions 1.0, 1.1 
	- Microsoft Visual InterDev, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are automating the MSDEV.exe Debugger object, the SetNextStatement
	method displays the following message:
	
	  This operation will move the current location to a different function.
	
	CAUSE
	=====
	
	The target line number of the SetNextStatement method is outside the scope of
	the current function. The message is not suppressed during automation.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	The error message alerts the operator that this action, while permitted, might
	cause unexpected behavior. It appears normally when you click Set Next Statement
	from the debugger's shortcut menu to move the code execution location to another
	function. However, during automation, this sort of informational message box
	should never appear.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a default MFC .exe application. Name it SetNext.
	
	2. From the ClassView window, expand the CSetNextDoc class. Double-click
	  CSetNextDoc().
	
	3. Click on the curly brace at the beginning of the function (at or near line
	  31). Press the F9 key once to set a breakpoint there. The code should look
	  something like the following:
	
	  ...
	  30: CSetNextDoc::CSetNextDoc()
	  31:>{
	  32:    // TODO: add one-time construction code here
	  33: }
	  34:
	  35: CSetNextDoc::~CSetNextDoc()
	  36: {
	  37: }
	  ...
	
	  The line numbers are added for illustration only. The > represents a line
	  with a set breakpoint.
	
	4. Create a Visual Basic Script macro named SetNext. To do this, go to the Tools
	  menu, click Macro, type "SetNext" (without the quotation marks) in the Macro
	  Name field, and click Edit. Click OK on the Add Macro dialog box. Replace the
	  SetNext subroutine with the following text and press Ctrl+S to save the macro
	  file:
	
	  Sub SetNext()
	     Debugger.RunToCursor
	     Debugger.SetNextStatement 36, "SetNextDoc.cpp"
	  End Sub
	
	  In this example, 36 represents a valid line in another function of the same
	  source file of the SetNext application.
	
	5. On the File menu, click Close. This closes the Macro window.
	
	6. Execute the SetNext VBScript macro. To do this, go to the Tools menu, click
	  Macro, click OK on any informational dialog boxes, and double-click SetNext
	  in the Macro Name list.
	
	RESULT: The message described in the SYMPTOMS section appears. Click OK to
	dismiss it. On the Debug menu, click Stop Debugging.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAutomation kbide kbVC500 kbVC600 kbVCObj kbVisID100 kbVJ100 kbVJ110 kbVS97 kbDevStudio kbGrpDSTools 
	Technology        : kbVCsearch kbVJsearch kbVisIDsearch kbAudDeveloper kbVC500 kbVC600 kbVC32bitSearch kbVisID100 kbVJ100 kbVJ110 kbVC500Search
	Version           : WINDOWS:1.0,1.1,97; winnt:5.0,6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
