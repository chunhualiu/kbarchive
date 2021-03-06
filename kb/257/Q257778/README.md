---
layout: page
title: "Q257778: BUG: Closing Two MDI Child Forms Rapidly Results in an IPF"
permalink: /kb/257/Q257778/
---

## Q257778: BUG: Closing Two MDI Child Forms Rapidly Results in an IPF

{% raw %}

	Article: Q257778
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0; Win2000:95
	Operating System(s): 
	Keyword(s): kbVBp kbVBp600bug kbOSWin95 kbIDEProject kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5f
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you have a Visual Basic 6.0 Service Pack 3 multiple-document interface (MDI)
	project and you close two MDI Child Forms in rapid succession, you can cause the
	following Invalid Page Fault (IPF) error message to occur:
	
	  VB6 caused an invalid page fault in
	  module VB6.EXE at 0137:00420268.
	
	Followed by this error message:
	
	  VB6 caused an invalid page fault in
	  module SSSCC.DLL at 0137:60567702.
	
	The problem only happens in the Visual Basic Integrated Development Environment
	(IDE) on Microsoft Windows 95, and not as a compiled executable.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a bug in the Microsoft products that are
	listed at the beginning of this article. This bug was corrected in the latest
	service pack for Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the following
	article numbers to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	To download the latest Visual Studio service pack, visit the following Microsoft
	Web site:
	
	  http://msdn.microsoft.com/vstudio/downloads/updates.asp
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. From the Project menu, add a new MDI form, a new Form, a new Class Module,
	  and a new UserControl object to the project.
	
	3. On the Project menu, and click to select Project1 Properties. On the General
	  tab, set the Startup Object to MDIForm1.
	
	4. With MDIForm1 visible, go to the Tools menu, and click to select the Menu
	  Editor. Create one new menu item with the following properties:
	
	+------------------------+
	| Caption | Load Forms   | 
	+------------------------+
	| Name    | mnuLoadForms | 
	+------------------------+
	
	5. Set Form1 and Form2's MDIChild Property = True.
	
	6. On the Project menu, click to select Components. Select Microsoft Windows
	  Common Controls 6.0 and click OK.
	
	7. Add a Toolbar control to UserControl1.
	
	8. Right-click on Toolbar1 and select Properties. Select the Buttons tab, and
	  click Inset Button to add a new button to Toolbar1. Set the Caption Property
	  to Exit.
	
	9. Close the design window for the UserControl and place an instance of
	  UserControl1 on Form1 and Form2.
	
	10. Paste the following code into MDIForm1:
	
	  Option Explicit
	
	  Private Sub mnuLoadForms_Click()
	      
	      Form1.Show
	      Form2.Show
	      
	  End Sub
	
	11. Paste the following code into the code windows of Form1 and Form2:
	
	  Option Explicit
	
	  Implements Class1
	
	  Private Sub Class1_UnloadForm()
	      
	      Unload Me
	      
	  End Sub
	
	  Private Sub Form_Load()
	
	      UserControl11.AddControl Me
	
	  End Sub
	
	12. Paste the following code into Class1:
	
	  Option Explicit
	
	  Public Sub UnloadForm()
	  '
	  End Sub
	
	13. Paste the following code into UserControl1:
	
	  Option Explicit
	
	  Private ucCollection As Collection
	
	  Public Sub AddControl(Item As Class1)
	      
	      ucCollection.Add Item
	      
	  End Sub
	
	  Private Sub Toolbar1_ButtonClick(ByVal Button As MSComctlLib.Button)
	  Dim cls As New Class1
	
	      Set cls = ucCollection.Item(1)
	
	      cls.UnloadForm
	
	      Set cls = Nothing
	      
	  End Sub
	
	  Private Sub UserControl_Initialize()
	      
	      Set ucCollection = New Collection
	      
	  End Sub
	
	  Private Sub UserControl_Terminate()
	
	      Set ucCollection = Nothing
	
	  End Sub
	
	14. Save and run the project. Select the Load Forms menu to load Form1 and
	  Form2. Then click on the Exit button on both forms in rapid succession. You
	  should see the IPF that is listed in the "Symptoms" section of this article.
	
	Additional query words: sp4 GPF
	
	======================================================================
	Keywords          : kbVBp kbVBp600bug kbOSWin95 kbIDEProject kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix 
	Technology        : kbVBSearch kbAudDeveloper kbWin95search kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600 kbZNotKeyword3
	Version           : WINDOWS:6.0; Win2000:95
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
