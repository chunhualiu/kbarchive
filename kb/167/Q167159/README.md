---
layout: page
title: "Q167159: WD97: IPF Creating New Blank Web Page Template"
permalink: /kb/167/Q167159/
---

## Q167159: WD97: IPF Creating New Blank Web Page Template

{% raw %}

	Article: Q167159
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbusage kbtemplate
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you create a new document template based on the Blank Web Page template,
	you receive the following error message:
	
	  This program has performed an illegal operation and will be shutdown.
	
	  If the problem persists, contact the program vendor.
	
	When you click Details, the following message appears:
	
	  WINWORD caused an invalid page fault in module WINWORD.EXE at
	  0137:<address>.
	
	Saving and closing the file before you create the document template based on the
	Blank Web Page template does not prevent the error message.
	
	NOTE: This problem does not occur if you create a new document based on the Blank
	Web Page template.
	
	CAUSE
	=====
	
	This problem occurs when both of the following are true:
	
	- You use any command on the Insert menu.
	
	  -and-
	
	- You create a new document template based on the Blank Web Page template.
	
	WORKAROUND
	==========
	
	Method 1: Insert the object from a toolbar
	------------------------------------------
	
	To insert a text box, a WordArt object, or an AutoShape object, click the
	corresponding button on the Drawing toolbar.
	
	To insert a picture object, click the Insert Picture button on the Picture
	toolbar.
	
	To insert a frame, add the InsertFrame command to another menu or a toolbar. For
	information about how to do this, see "Method 2: Add or move the command to
	another menu."
	
	Method 2: Add or move the command to another menu
	-------------------------------------------------
	
	For information about customizing, creating, and restoring Word menus and
	toolbars, please see the following articles in the Microsoft Knowledge Base:
	
	  Q155800 WD97: How to Customize, Create, and Restore Word Menus/Toolbars
	
	  Q163547 WD97: How to Create Custom Toolbars and Toolbar Buttons
	
	For more information about creating custom menus, click the Office Assistant,
	type "custom menu," click Search, and then click to view "Add a command or other
	item to a menu."
	
	For more information about copying or moving menu items, click the Office
	Assistant, type "move menu," click Search, and then click to view "Move or copy
	a menu command."
	
	NOTE: If the Assistant is hidden, click the Office Assistant button on the
	Standard toolbar. If Word Help is not installed on your computer, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q120802 Office: How to Add/Remove a Single Office Program or Component
	
	Method 3: Create a document and then save it as a template
	----------------------------------------------------------
	
	After you use a command on the Insert menu, create a document based on the Blank
	Web Page template. To create a new document based on the Blank Web Page
	template, use the following steps:
	
	1. On the File menu, click New, and click the Web Pages tab.
	
	2. Click the Blank Web Page template.
	
	3. Under Create New, click Document.
	
	4. Click OK.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	Additional query words: ipf
	
	======================================================================
	Keywords          : kbusage kbtemplate 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Hardware          : x86
	
	=============================================================================
	

{% endraw %}
