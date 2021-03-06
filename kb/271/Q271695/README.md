---
layout: page
title: "Q271695: PRB: Picture in MDI Form Does Not Display"
permalink: /kb/271/Q271695/
---

## Q271695: PRB: Picture in MDI Form Does Not Display

{% raw %}

	Article: Q271695
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 6.0
	Operating System(s): 
	Keyword(s): kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When programmatically setting the picture property of a multiple-document
	interface (MDI) Form, the picture may not be displayed, or may be partially
	rendered when an MDIChild form is dragged inside the MDI Form.
	
	This behavior does not occur in Microsoft Visual Basic 5.0.
	
	RESOLUTION
	==========
	
	Use the RedrawWindow API function to redraw the MDI Form after the picture
	assignment.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a Visual Basic 6.0 Standard EXE project. Form1 is created by default.
	
	2. On the Properties window, set following properties for Form1:
	
	  MDIChild = True
	
	3. On the Project menu, click Add MDIForm to add a MDI Form.
	
	4. On the Properties window, set following properties for MDIForm1:
	
	  WindowState = 2 - Maximized
	
	5. on the Project menu, select Properties. On the General tab, select MDIForm1
	  as the Startup Object, and then modify MDIForm1's Load event as follows:
	
	  Private Sub MDIForm_Load()
	      'Show the Child Form
	      Form1.Show 
	  End Sub
	
	6. Add a CommandButton to Form1. Modify the button's click event as follows:
	
	  Private Sub Command1_Click()
	      'Assign picture
	      MDIForm1.Picture = LoadPicture("c:\winnt\winnt.bmp")
	  End Sub
	
	7. Start the application, and then drag Form1 from its default position toward
	  the center of the screen.
	
	8. Click the CommandButton on Form1, and note that no picture appears. The
	  expected behavior is that the picture appears if you drag Form1 to the
	  top-left corner of MDIForm1.
	
	Workaround
	----------
	
	In order to work around this behavior, you can call RedrawWindow after assigning
	a picture to the MDIForm's picture property. This causes the MDIForm to redraw
	and display the picture.
	
	1. On the Project menu, click Add Module to add a new module to the project.
	
	2. Paste the following code into the new module:
	
	  Public Declare Function RedrawWindow Lib "user32" (ByVal hWnd As Long, lprcUpdate As Any, _  
	  ByVal hrgnUpdate As Long, ByVal fuRedraw As Long) As Long
	  Public Const RDW_ALLCHILDREN = &H80
	  Public Const RDW_ERASE = &H4
	  Public Const RDW_INVALIDATE = &H1
	  Public Const RDW_UPDATENOW = &H100
	
	3. Modify the Command_Click Event on Form1 thus:
	
	  Private Sub Command1_Click()
	      'Assign picture
	      MDIForm1.Picture = LoadPicture("c:\winnt\winnt.bmp")
	      'Redraw Window
	      Call RedrawWindow(MDIForm1.hWnd, ByVal 0&, 0&, _ 
	           RDW_ERASE Or RDW_INVALIDATE Or RDW_ALLCHILDREN Or RDW_UPDATENOW)
	  End Sub
	
	4. Start the application, and then drag Form1 toward the center of the screen.
	
	5. Click the Command Button on Form1, and note that the picture is displayed.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : :6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
