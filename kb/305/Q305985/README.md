---
layout: page
title: "Q305985: HOWTO: Add Functionality to Your Dynamically Built Grid"
permalink: /kb/305/Q305985/
---

## Q305985: HOWTO: Add Functionality to Your Dynamically Built Grid

{% raw %}

	Article: Q305985
	Product(s): Microsoft FoxPro
	Version(s): 3.0,3.0b,5.0,5.0a,6.0,7.0
	Operating System(s): 
	Keyword(s): kbContainer kbCtrl kbvfp kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport kb
	Last Modified: 30-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0, 7.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Although a grid has its own events, the events do not always fire when you would
	expect them to. Because a grid is a container control, the objects in the
	container receive the events. Therefore, to add functionality to a grid, you
	must add the method code to the text boxes (or other controls) that display the
	data. However, you cannot add code to objects at run time.
	
	MORE INFORMATION
	================
	
	Because you cannot add code to objects at run time, you must use a custom class
	for your text boxes. The grid, however, does its best to display the table as if
	you were browsing it, so you need to be careful about the order in which you do
	things. You can also add code to custom header classes; for example, code to
	sort the grid by the column that you click.
	
	The following code displays a message box when you double-click the displayed
	data. If you double-click below or to the right of the data, the grid DblClick
	event fires instead.
	
	  PUBLIC loForm
	
	  CD HOME() 
	
	  *!* Make sure that the grid doesn't pick this up automatically
	  USE labels IN 1
	  SELECT 25  && Temporally select blank work area.
	
	  loForm = CREATEOBJECT("Form")
	  loForm.AddObject("grdLabels", "grdName")
	
	  WITH loForm.grdLabels
	     .AddObject("colName", "Column")
	     *!* We now have a Grid with a single column containing a header
	     *!* and a textbox.
	     
	     .colName.Width = 200
	
	     *!* If this is set before the columns are defined, the
	     *!* grid picks up the columns it thinks it needs.
	     .RecordSourceType = 1
	     .RecordSource = "labels"
	     
	     .colName.ControlSource = "labels.name"
	     .colName.Header1.Caption = "Label name"
	
	     *!* Now we add our custom textbox control, and remove the original.
	     .colName.AddObject("txtName", "txtGrid")
	     .colName.txtName.BorderStyle = 0
	     .colName.CurrentControl = "txtName"
	     .colName.RemoveObject("Text1")
	
	     *!* The default visibility for all objects added with AddObject is .F.
	     .colName.Visible = .T.
	     .Visible = .T.
	  ENDWITH
	
	  loForm.Visible = .T.
	
	  DEFINE CLASS txtGrid AS TextBox
	     PROCEDURE DblClick
	        =MESSAGEBOX(STR(RECNO()))
	     ENDPROC
	  ENDDEFINE
	
	  DEFINE CLASS grdName AS Grid
	     PROCEDURE DblClick
	        =MESSAGEBOX("You didn't click on the data.")
	     ENDPROC
	  ENDDEFINE
	
	REFERENCES
	==========
	
	For additional information about grids and their events, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q128075 PRB: Grid Does Not Respond to the Click or DblClick Events
	
	Additional query words:
	
	======================================================================
	Keywords          : kbContainer kbCtrl kbvfp kbvfp300b kbvfp500 kbvfp500a kbvfp600 kbGrpDSFox kbDSupport kbCodeSnippet kbvfp300xSearch kbvfp500xSearch kbvfp700 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP700 kbVFP500a
	Version           : :3.0,3.0b,5.0,5.0a,6.0,7.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
