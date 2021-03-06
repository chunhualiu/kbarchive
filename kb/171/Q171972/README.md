---
layout: page
title: "Q171972: FIX: Cannot Disable UserControl on Modal Form"
permalink: /kb/171/Q171972/
---

## Q171972: FIX: Cannot Disable UserControl on Modal Form

{% raw %}

	Article: Q171972
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A UserControl created in Visual Basic and placed on a form that is opened
	modally does not respond to attempts made to disable it. Setting the Enabled
	property of the control behaves as expected on a non-modal form, but setting
	Enabled = False on a modal form has no effect.
	
	RESOLUTION
	==========
	
	You can use the Windows API function EnableWindow to enable/disable the ActiveX
	control.
	
	1. In the General Declaration section of the module, place the following
	  declaration: (This must be declared as Private if it is included in a form
	  module.)
	
	        Private Declare Function EnableWindow Lib "user32" Alias _
	           "EnableWindow" (ByVal hwnd As Long, ByVal fEnable As Long) As Long
	
	2. The hWnd property, like all UserControl properties, requires a public
	  property method to expose the property as part of the object's interface.
	  Since you will not be setting a value, the Property Get is all that is
	  needed.
	
	        Public Property Get hWnd() as Long
	           hWnd=UserControl.hWnd
	        End Property
	
	3. Next, you need to associate this method with the hWnd property of the
	  control:
	
	  a. From the Tools menu, select Procedure Attributes.
	
	  b. Select "hWnd" from the Name drop-down list.
	
	  c. Click the Advanced button.
	
	  d. From the Procedure ID drop-down list, choose "hWnd." Click OK.
	
	4. The EnableWindow function can now be called to enable or disable the
	  UserControl. To disable the UserControl:
	
	        Dim result as Long
	        result = EnableWindow(Me.UserControl1.hWnd, 0)
	
	  To enable the UserControl:
	
	        Dim result as Long
	        result = EnableWindow(Me.UserControl1.hWnd, 1)
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Basic 6.0.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new "ActiveX Control" project.
	
	2. Add the following code to the UserControl:
	
	        Public Property Get enabled() As Boolean
	             enabled = UserControl.enabled
	        End Property
	
	        Public Property Let enabled(vNewValue As Boolean)
	             UserControl.enabled = vNewValue
	        End Property
	
	        Private Sub UserControl_Click()
	            MsgBox "Control is not Disabled."
	        End Sub
	
	3. From the Tools menu, select Procedure Attributes.
	
	4. Click the Advanced button.
	
	5. From the Procedure ID drop-down, chose "Enabled." Click OK.
	
	6. Add a "Standard EXE" project.
	
	7. Close the UserControl window, and add the UserControl to Form1.
	
	8. Add two CommandButtons to Form1. Set the following properties.
	
	     Name: Command1    Caption: "Enable Control"
	     Name: Command2    Caption: "Disable Control"
	
	9. Add the following code to Form1.
	
	        Private Sub Command1_Click()
	           Me.UserControl11.Enabled = True
	        End Sub
	
	        Private Sub Command2_Click()
	           Me.UserControl11.Enabled = False
	        End Sub
	
	10. Add a standard module to the project.
	
	11. Add the following code to Module1:
	
	        Public Sub Main()
	               Form1.Show vbModal
	             End Sub
	
	12. Run the project.
	
	13. Note that clicking on the button labeled "Disable Control" does not prevent
	  the message box from appearing when the UserControl is clicked.
	
	14. Stop the project and open Module1.
	
	15. In Sub Main(), change:
	
	         Form1.Show vbModal
	
	  to:
	
	         Form1.Show
	
	16. Run the project again, and note that the "Disable Control" button now
	  functions as expected and the message box does not appear.
	
	Additional query words: kbComp kbCtrl kbVBp kbdsd kbVBp500bug kbVBp600fix kbDSupport kbCtrlCreate kbAPI
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbZNotKeyword3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
