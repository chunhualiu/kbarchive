---
layout: page
title: "Q239943: FIX: UserControls with Menus Cause Resource Leak"
permalink: /kb/239/Q239943/
---

## Q239943: FIX: UserControls with Menus Cause Resource Leak

	Article: Q239943
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbActiveX kbAPI kbCtrl kbMenu kbSDKWin32 kbVBp kbVBp500bug kbVBp600bug kbGrpDSVB kbDSup
	Last Modified: 26-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a usercontrol has any top level menus where the NegotiateMenus property is
	non-zero, resources drain slowly when the focus is set to and from the
	usercontrol. The problem occurs in both the Visual Basic Design Environment
	(IDE) and as an EXE.
	
	CAUSE
	=====
	
	Visual Basic destroys the UserControl's main menu, but does not destroy all of
	the submenus under the main menu when the UserControl loses input focus.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in the latest service pack for
	Visual Studio 6.0.
	
	For additional information about Visual Studio service packs, click the article
	numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q194022 INFO: Visual Studio 6.0 Service Packs, What, Where, Why
	
	  Q194295 HOWTO: Tell That a Visual Studio Service Pack Is Installed
	
	You can download the latest Visual Studio service pack from the following
	Microsoft Web site:
	
	  Visual Studio Product Updates
	  (http://msdn.microsoft.com/vstudio/downloads/updates.asp)
	
	MORE INFORMATION
	================
	
	Steps to Reproduce and Work Around the Problem:
	
	1. Start a new Visual Basic Standard EXE project. Form1 is created by default.
	  The NegotiateMenus property of Form1 is set to True by default.
	
	2. On the Project menu, click Add User Control to add UserControl1 to the
	  project.
	
	3. Add a CommandButton and a CheckBox control to UserControl1.
	
	4. Create a menu with several items and sub items on UserControl1. Set the
	  NegotiatePosition property of each top level menu item to 1-Left.
	
	5. Add the following code to the General Declarations section of UserControl1:
	
	  Option Explicit
	  '
	  '
	  ' Demonstrates how to free menu resources orphaned by a UserControl.
	
	  ' Zero-based array and one-based counter
	  ' of cached UserControl submenus
	
	  Private m_ahMenus() As Long
	  Private m_nMenus As Integer
	
	  Private Declare Function GetMenu Lib "user32" (ByVal hwnd As Long) As Long
	  Private Declare Function GetSubMenu Lib "user32" (ByVal hMenu As Long, _
	     ByVal nPos As Long) As Long
	  Private Declare Function GetMenuItemCount Lib "user32" _
	     (ByVal hMenu As Long) As Long
	  Private Declare Function IsMenu Lib "user32" (ByVal hMenu As Long) As Long
	  Private Declare Function DestroyMenu Lib "user32" (ByVal hMenu As Long) _
	     As Long
	
	  Private Declare Function GetParent Lib "user32" (ByVal hwnd As Long) As Long
	
	  Private Sub UserControl_EnterFocus()
	     ' the UserControl's main menu has been created and has
	     ' replaced the form's main menu before any control on the
	     ' UserControl gains input focus.
	
	     If Check1.Value And (m_nMenus = 0) Then
	        Call LoadMenus(GetMenu(GetParent(UserControl.hwnd))) ' Form1.hwnd))
	        Debug.Print "UserControl submenus loaded: " & m_nMenus
	     End If
	  End Sub
	
	  Private Sub UserControl_ExitFocus()
	     ' the UserControl's main menu has been destroyed, and has
	     ' replaced been by the form's main menu. *But* all submenus
	     ' under UserControl's main menu have not been destroyed.
	
	     If m_nMenus Then
	        Debug.Print "UserControl submenus destroyed: " & DestroyMenus
	     End If
	  End Sub
	
	  Private Sub UserControl_Initialize()
	     Check1.Caption = "Workaround"
	     BorderStyle = 1
	  End Sub
	
	  Private Sub Check1_Click()
	     If (Check1.Value = vbChecked) And (m_nMenus = 0) Then
	        Call LoadMenus(GetMenu(GetParent(UserControl.hwnd)))
	        Debug.Print "UserControl submenus loaded: " & m_nMenus
	     ElseIf (Check1.Value = vbUnchecked) And m_nMenus Then
	        Erase m_ahMenus ' Clear the module level variables
	        m_nMenus = 0
	        Debug.Print "No UserControl submenus will be destroyed"
	     End If
	  End Sub
	
	  ' Pass the UserControl's top level menu on first call
	
	  Private Sub LoadMenus(hMenu As Long)
	     Dim nItems As Integer
	     Dim i As Integer
	     Dim hSubmenu As Long
	     
	     nItems = GetMenuItemCount(hMenu)
	
	     For i = 0 To nItems - 1
	        hSubmenu = GetSubMenu(hMenu, i)
	
	        If IsMenu(hSubmenu) Then
	           ReDim Preserve m_ahMenus(m_nMenus)
	           m_ahMenus(m_nMenus) = hSubmenu
	           m_nMenus = m_nMenus + 1
	        End If
	
	        Call LoadMenus(hSubmenu) ' recurse through sub menu
	     Next
	  End Sub
	
	  Private Function DestroyMenus() As Integer
	     Dim i As Integer
	     Dim n As Integer
	
	     For i = m_nMenus - 1 To 0 Step -1
	        If IsMenu(m_ahMenus(i)) Then
	           ' Will destroy all submenus under the current submenu, toggle the
	           ' For expression comments above to destroy individual submenus.
	           Call DestroyMenu(m_ahMenus(i))
	           n = n + 1
	        End If
	     Next
	
	    ' Clear the mod level variables
	     Erase m_ahMenus
	     m_nMenus = 0
	
	     DestroyMenus = n
	
	  End Function
	
	6. Close all of UserControl1's open windows.
	
	7. Add a CommandButton and a UserControl1 to Form1. UserControl11 is created by
	  default.
	
	8. Add the following code to the General Declarations section of Form1:
	
	  Private Sub Form_Click()
	     Dim i As Integer
	     For i = 1 To 2000
	        UserControl11.SetFocus
	        DoEvents ' IMPORTANT:  Allows SetFocus to complete before proceeding
	        Command1.SetFocus
	        DoEvents
	        Me.Caption = i
	     Next i
	  End Sub
	
	9. Save your project.
	
	10. On Windows 95, Windows 98, or Windows Me, start the Resource Meter. The
	  Windows NT or Windows 2000 Task Manager does not provide the same level of
	  functionality.
	
	11. Run the project, and click on the form. Under Win9x, the Resource Meter
	  shows a steady decline in User and System resources.
	
	12. Click the form again. On most systems, you observe problems with
	  menu-related functionality such as Copy, Paste, and the Start menu. You may
	  also see changes to fonts and icons used by the system.
	
	13. Click the Stop button. You may receive an Out of Memory dialog, which you
	  can dismiss. Terminate the Visual Basic IDE and observe that the resources
	  are released.
	
	14. Restart the Visual Basic IDE. Reload and run your project.
	
	15. Select the checkbox labeled Workaround and click the form. The Resource
	  Meter shows no decline in resources.
	
	Additional query words: sp4
	
	======================================================================
	Keywords          : kbActiveX kbAPI kbCtrl kbMenu kbSDKWin32 kbVBp kbVBp500bug kbVBp600bug kbGrpDSVB kbDSupport kbVS600sp4fix kbVS600sp5fix kbbuglist
	Component         : Component
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Version           : :5.0,6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	