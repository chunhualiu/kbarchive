---
layout: page
title: "Q195162: HOWTO: Use the Batch File Generated by PDW"
permalink: /kb/195/Q195162/
---

## Q195162: HOWTO: Use the Batch File Generated by PDW

{% raw %}

	Article: Q195162
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:6.0
	Operating System(s): 
	Keyword(s): kbwizard kbAppSetup kbVBp kbVBp600
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Launching the Batch file generated by the Package and Deployment Wizard (PDW)
	after making changes to the control does not include the latest version of the
	control in the cab file. Therefore, the changes are not reflected when you
	launch the HTML file.
	
	MORE INFORMATION
	================
	
	Here are the steps to follow to make sure that the latest version of the control
	is included in the cab file:
	
	1. Compile your control after making/saving changes. Make sure that your control
	  is Binary Compatible. To make your control binary Compatible, follow these
	  steps:
	
	  a. Before making the OCX for the first time, go to project properties,
	     components tab and click the "no compatibility" button.
	
	  b. Go to file menu and select "make OCX."
	
	  c. Go back to the components tab under project properties and click the
	     "Binary compatible" button. Type the complete path of the .OCX file you
	     just created in the text box under that option, or click the command
	     button next to the text box, which will bring the file dialog box up where
	     you can select the .OCX file.
	
	  d. Click OK. Go back to the file menu and make the OCX. Make sure you select
	     the same OCX when prompted, and click "Yes" when asked if you want to
	     overwrite the previous OCX. This assures that the control is binary
	     compatible.
	
	2. Copy the new version of the OCX in the support directory generated by PDW, as
	  this is not updated.
	
	3. Modify the .INF file to change the version number under the section for this
	  control.
	
	4. Now run the batch file.
	
	5. Modify the .HTML file such that the codebase attribute has the version =
	  <the latest version number>.
	
	6. Now launch the HTML file and the new version of the control should be
	  downloaded on the client machine.
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q190046 : INFO: VB6 Readme Part 6 - Wizard Issues
	
	======================================================================
	Keywords          : kbwizard kbAppSetup kbVBp kbVBp600 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
