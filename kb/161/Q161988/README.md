---
layout: page
title: "Q161988: WD97: Full Screen View Toolbar Is Hidden"
permalink: /kb/161/Q161988/
---

## Q161988: WD97: Full Screen View Toolbar Is Hidden

{% raw %}

	Article: Q161988
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbualink97 kbdta kbdtacode kbmacroexample word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you view Full Screen (on the View menu, click Full Screen), the Full Screen
	toolbar is missing.
	
	CAUSE
	=====
	
	By design, Word does not provide a menu command to turn off the Full Screen
	toolbar. The only way to hide the Full Screen toolbar is to run a Visual Basic
	for Applications command.
	
	If the Full Screen toolbar is hidden, you may have a macro or add-in that has set
	the visible property for the Full Screen toolbar to False.
	
	WORKAROUND
	==========
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	If you are in Full Screen view and the Full Screen toolbar is not appearing, you
	can use the following methods to return from Full Screen view or to redisplay
	the Full Screen toolbar.
	
	Method 1: To Return from Full Screen View
	-----------------------------------------
	
	1. Press the ESC key on your keyboard.
	
	  -or-
	
	  Press ALT+V+U.
	
	  -or-
	
	2. Press ALT+T+M+M.
	
	3. In the Macro Name box, type "ToggleFull" (without the quotation marks).
	
	4. Click Run.
	
	If this does not work, it is possible that the ToggleFull macro has been altered
	from its default functionality.
	
	The following steps will restore the ToggleFull macro functionality:
	
	IMPORTANT: These steps involve deleting a macro. If you are unsure as to the
	source of the macro in question, you may want to investigate the source before
	proceeding. For example, if you are part of an administrative group in a network
	environment, check with your network administrator prior to deleting this
	macro.
	
	1. On the Tools menu, point to Macro, and then click Macros.
	
	2. From the "Macros in" box, select "All active templates and documents." If
	  ToggleFull appears as an available macro in the list of macros, select it.
	
	3. Click Delete.
	
	Method 2: To Redisplay the Full Screen Toolbar
	----------------------------------------------
	
	The following Visual Basic for Applications macro will redisplay the Full Screen
	toolbar.
	
	     Sub ShowFullScrToolBar()
	        If ActiveWindow.View.FullScreen Then
	           CommandBars("full screen").Visible = True
	        End If
	     End Sub
	
	NOTE: Before you run this macro, you must be in Full Screen view.
	
	To run this macro while in Full Screen view, follow these steps:
	
	1. Press ALT+T+M+M.
	
	2. In the Macro Name box, type "ShowFullScrToolBar" (without the quotation
	  marks).
	
	3. Click OK.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173707 OFF97: How to Run Sample Code from Knowledge Base Articles
	
	
	MORE INFORMATION
	================
	
	In Word 97, the Full Screen toolbar does not appear in the list of toolbars when
	you point to Toolbars on the View menu.
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	Additional query words: vb vba vbe
	
	======================================================================
	Keywords          : kbualink97 kbdta kbdtacode kbmacroexample word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
