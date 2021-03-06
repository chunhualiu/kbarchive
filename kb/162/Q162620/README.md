---
layout: page
title: "Q162620: BUG: Setup Incorrectly Prompts to Overwrite Existing Files"
permalink: /kb/162/Q162620/
---

## Q162620: BUG: Setup Incorrectly Prompts to Overwrite Existing Files

{% raw %}

	Article: Q162620
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbsetup kbVBp400bug kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run Setup files that you created with the Visual Basic Application
	Setup Wizard, the following warnings appear:
	
	  Setup is about to replace a pre-existing file(s). This may cause loss of data
	  for an existing application.
	
	followed by:
	
	  Installing over an existing installation without first removing it may damage
	  that installation or cause future attempts to remove the installation to
	  fail.
	
	This warning occurs even when the files are marked as "shared" in the Application
	Setup Wizard.
	
	CAUSE
	=====
	
	If a Template is defined in step 7 (the final step) of the Application Setup
	Wizard the resulting .lst and .vbz are incorrect for system-shared files that
	you added manually in step 7.
	
	RESOLUTION
	==========
	
	1. Recreate your images without using your template and do not choose to save a
	  template in step 7 of the Application Setup Wizard. Save the template in the
	  Finish dialog box after the Application Setup Wizard has compressed all the
	  files.
	
	-or-
	
	2. Modify your existing .lst and .vbz files. In the .lst files, modify the 7th
	  field of the appropriate system file so it contains $(Shared). In the .vbz,
	  modify the 7th field so it contains -1. For example, when the warning occurs
	  referencing Mfcans32.dll, the .lst file looks like the following:
	
	  File5=1,,MFCANS32.DL_,MFCANS32.DLL,$(WinSysPath),,,6/21/1995,149504,3.2.0.0
	
	  and the .vbz file looks like:
	
	  File11=E:\vbtemp\MFCANS32.DLL,0,$(WinSysPath),,|32760|,-1,0,0,0,,,0
	
	  Modify the .lst file as follows:
	
	  File5=1,,MFCANS32.DL_,MFCANS32.DLL,$(WinSysPath),,$(Shared),6/21/1995,14950
	  4,3.2.0.0
	
	  and change the .vbz entry to:
	
	  File11=E:\vbtemp\MFCANS32.DLL,0,$(WinSysPath),,|32760|,-1,-1,0,0,,,0
	
	  The Template file (.vbz) should now be correct and generate correct images in
	  the future.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Visual Basic version
	4.0. Microsoft is researching this problem and will post new information here as
	it becomes available.
	
	MORE INFORMATION
	================
	
	When the Setup Wizard creates the template in step 7, it creates an incorrect
	.lst and .vbz file for the current images and all future images that use the
	template (.vbz).
	
	Specifically, it does not mark the system files as Shared in the .lst and .vbz
	files. Thus, when the Application Setup Wizard runs it does not correctly
	overwrite the system files that are older and it prompts the user with the
	warnings.
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Create a simple application and build it into an .exe.
	
	2. Start the Application Setup Wizard.
	
	3. Point to the Visual Basic Application created in step 1.
	
	4. Click Next until you arrive at step 3 and point it to an empty directory on
	  your hard drive.
	
	5. Click Next until you arrive at step 7 (the final step).
	
	6. In step 7, click "Add Files...".
	
	7. Select a system DLL, such as Mfcans32.dll from your \Windows\System32
	  subdirectory, and then click OK.
	
	8. Now Select the DLL that you just added in the list box and click "Files
	  Details...".
	
	9. Note that it says "Install as a Shared File." Click OK.
	
	10. Click Save Template.
	
	11. Name the template file and click Save.
	
	12. Click Finish.
	
	13. Edit the .vbz and the .lst. Note that it is incorrect.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsetup kbVBp400bug kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbVB400Search kbVB400
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
