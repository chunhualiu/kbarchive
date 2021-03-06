---
layout: page
title: "Q117838: FIX: SETUP.EXE Does Not Check for Available Disk Space"
permalink: /kb/117/Q117838/
---

## Q117838: FIX: SETUP.EXE Does Not Check for Available Disk Space

{% raw %}

	Article: Q117838
	Product(s): Microsoft FoxPro
	Version(s): 2.5x,2.6x
	Operating System(s): 
	Keyword(s): kberrmsg kbsetup
	Last Modified: 24-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FoxPro for Windows Distribution Kit, versions 2.5x, 2.6x 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	SETUP.EXE in the FoxPro for Windows Distribution Kit, specifically the SETUP.APP
	Setup Wizard, does not successfully measure the amount of disk space on the
	destination system before beginning the actual installation of the application.
	This is despite the message SETUP displays saying that it will check for
	available disk space.
	
	If the destination drive does not have enough free disk space, SETUP proceeds
	until it encounters a situation in which the available space is less than that
	required to expand and load the next file from the distribution disk. When this
	situation occurs, SETUP displays the error message "Cannot Write
	<filename>."
	
	WORKAROUND
	==========
	
	Use one of the following workarounds:
	
	1. At an MS-DOS prompt, type the following:
	
	           C:\FPW26\DKSETUP\DECOMP DISK1\SETUP.MS_ C:\SETUP.MST
	           EDIT C:\SETUP.MST
	
	2. From the Search menu choose Find.
	
	3. In the Find dialog box, "type dialogs%" (without the quotation marks).
	
	4. Change the text dialogs% to "dialog%" (without the quotation marks).
	
	5. Save and close the file.
	
	6. At an MS-DOS prompt, type the following:
	
	  C:\FPW26\DKSETUP\COMPRESS C:\SETUP.MST DISK1\SETUP.MS_
	
	  The Setup Wizard will now work properly.
	
	-or-
	
	- Developers using the Distribution Kit for FoxPro for Windows should include
	  documentation with their distributed applications advising the end user of
	  the amount of hard disk space required to install the application. This space
	  requirement is in addition to the space required for the end user's tables
	  and working storage.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem was corrected in Visual FoxPro 3.0
	for Windows.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Problem
	--------------------------
	
	1. Copy the MS-DOS directory into the FoxPro directory.
	
	2. Package this MS-DOS directory, specifying ATTRIB.EXE as the master program.
	  Answer the Setup Wizard's questions by selecting the suggested default
	  values. Specify the appropriate size of floppy disks for the destination
	  machine (for example, 1.44 MB). Include in the distribution file set the
	  appropriate .ESL library for the release of FoxPro on the source machine.
	  (The wizard will request this.)
	
	3. Copy the files within the disk images to the appropriate sized disks. The
	  combined files will require approximately 6 MB of disk space.
	
	4. Fill the hard disk of the destination machine with enough copies of FPW26 (or
	  some other directory) to reduce the available space to less than the file
	  requirements of the distributed application (MS-DOS).
	
	5. From the Windows File menu, choose Run, and run SETUP from the floppy drive
	  into which the distribution disks fit.
	
	Additional query words: FoxWin VFoxWin 3.00 2.50 2.50a 2.50b 2.60 2.60a fixlist3.00 buglist2.50 buglist2.50a buglist2.50b buglist2.60 buglist2.60a dk setupwizard diskette errmsg err msg
	
	======================================================================
	Keywords          : kberrmsg kbsetup 
	Technology        : kbAudDeveloper kbFoxproSearch kbFoxProDK250xSearch kbFoxProDK260x kbFoxProDKSearch
	Version           : :2.5x,2.6x
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
