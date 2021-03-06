---
layout: page
title: "Q150202: BUG: Sheridan Frame and Panel Stretch Font with Move Method"
permalink: /kb/150/Q150202/
---

## Q150202: BUG: Sheridan Frame and Panel Stretch Font with Move Method

{% raw %}

	Article: Q150202
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0
	Operating System(s): 
	Keyword(s): kbVBp400bug
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If the Move method is invoked on a Sheridan Frame or Panel control, the font is
	stretched if the size of the control is modified by the Move method.
	
	RESOLUTION
	==========
	
	- Since this behavior does not occur with the Microsoft Frame control, use it
	  instead of the Sheridan Frame control.
	
	- Instead of using the Move method to resize the control, the width and height
	  of the control can be adjusted directly. For example, the following code
	  makes the Frame the same height and width as the form, and places its upper
	  left hand corner to the upper left hand corner of the form:
	
	        SSFrame1.Move 0, 0, Form1.ScaleWidth, Form1.ScaleHeight
	
	- Replace the line of code above with:
	
	        SSFrame1.Width = Form1.ScaleWidth
	
	        SSFrame1.Height = Form1.ScaleHeight
	
	        SSFrame1.Left = Form1.ScaleLeft
	
	        SSFrame1.Top = Form1.ScaleTop
	
	This code will not stretch the Caption of the control.
	
	STATUS
	======
	
	Microsoft has confirmed this to be an issue in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Start a new project in Visual Basic. Form1 is created by default.
	
	2. Place a Sheridan Frame control on Form1. If the Sheridan controls are not
	  visible in the Toolbox, from the Tools menu, select Custom Controls, and then
	  select Sheridan 3D Controls. In the Form_Click event, place the following
	  code:
	
	        Private Sub Form_Click()
	        SSFrame1.Move 0, 0, Form1.ScaleWidth, Form1.ScaleHeight
	
	        End Sub
	
	3. Run the project by pressing the F5 key. Click on the Form, and notice that
	  the Font for the caption of the frame control is stretched.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVBp400bug 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400 kbVB16bitSearch
	Version           : WINDOWS:4.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
