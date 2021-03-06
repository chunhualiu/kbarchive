---
layout: page
title: "Q194912: FIX: Add Method of Forms Collection Fails in Executable"
permalink: /kb/194/Q194912/
---

## Q194912: FIX: Add Method of Forms Collection Fails in Executable

{% raw %}

	Article: Q194912
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbservicepack kbVBp kbVBp500bug kbVBp600bug kbGrpDSVB kbVS600sp2 kbVS600SP1 kbVS
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You are using the Add method of the Forms collection to load a form. The code
	works correctly in the Visual Basic development environment, but fails with the
	following error when the application is made into an executable:
	
	  Run-time error '-2147417848 (80010108)':
	  Automation error.
	
	RESOLUTION
	==========
	
	You can work around this problem by creating your own Forms collection. A
	reference to the form can be added to a collection, and keyed by the Form's
	name. This will let you load a form by specifying a text string and referencing
	the matching key field in the collection.
	
	There are two options with this approach. You can pre-load the collection with a
	reference to all of the forms in the application at startup, which is the
	approach used in the following example. You may also load the forms into the
	collection as needed. There is slightly more programmatic overhead with the
	second approach, because you must check to see if the form is already in the
	collection. It is also important to note that adding the forms to the collection
	does not load the forms.
	
	Steps to work around this problem are:
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. From the Project menu, add a second form to the project.
	
	3. From the Project menu, add a standard module to the project.
	
	4. Add the following code to the code window of Form1:
	
	        Private Sub Form_Click()
	           Dim strFormToLoad As String
	           strFormToLoad = "Form2"
	           loadForm (strFormToLoad)
	        End Sub
	
	        Private Sub Form_Load()
	           colForms.Add Form2, "Form2"
	        End Sub
	
	5. Add the following code to Module1:
	
	        Public colForms As New Collection
	
	        Public Sub loadForm(strFormName As String)
	           Dim frm As Form
	           Set frm = colForms(strFormName)
	           frm.Show
	
	        End Sub
	
	6. Run the project and click on Form1.
	
	7. Form2 should be loaded.
	
	8. Stop the project.
	
	9. Choose Make Project1.exe from the File menu.
	
	10. Run Project1.exe, and click on Form1.
	
	11. Form2 should load successfully.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug was corrected in Visual Studio 6.0 Service Pack 3. For more information
	about Visual Studio service packs, please see the following articles in the
	Microsoft Knowledge Base:
	
	Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	Q194295 HOWTO: Tell That Visual Studio 6.0 Service Packs Are Installed
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. From the Project menu, add a second form to the project.
	
	3. From the Project menu, add a standard module to the project.
	
	4. Add the following code to the code window of Form1:
	
	        Private Sub Form_Click()
	           Dim strFormToLoad As String
	           strFormToLoad = "Form2"
	           loadForm (strFormToLoad)
	        End Sub
	
	5. Add the following code to Module1:
	
	        Public Sub loadForm(strFormName As String)
	           Dim frm As Form
	           Set frm = Forms.Add(strFormName)
	           frm.Show
	
	        End Sub
	
	6. Run the project, and click on Form1.
	
	7. Form2 should be loaded.
	
	8. Stop the project.
	
	9. Choose Make Project1.exe from the File menu.
	
	10. Run Project1.exe, and click on Form1.
	
	11. You should receive the error message listed above.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbcode kbservicepack kbVBp kbVBp500bug kbVBp600bug kbGrpDSVB kbVS600sp2 kbVS600SP1 kbVS600sp3fix kbCodeSam 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
