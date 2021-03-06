---
layout: page
title: "Q136973: PPT7: Sorry, PowerPoint Could Not Start or Locate 'PPT Tools'"
permalink: /kb/136/Q136973/
---

## Q136973: PPT7: Sorry, PowerPoint Could Not Start or Locate 'PPT Tools'

{% raw %}

	Article: Q136973
	Product(s): Microsoft PowerPoint for Windows
	Version(s): WINDOWS:7.0
	Operating System(s): 
	Keyword(s): kbsetup kbdtakbbuglist
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft PowerPoint for Windows 95, version 7.0 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	When you try to start the AutoContent Wizard, you may get the following error
	message:
	
	  Sorry, PowerPoint could not start or locate 'PPT Tools.' You should run Setup
	  and reinstall.
	
	You may also experience other symptoms such as:
	
	- The Quick Preview will not run.
	
	- There is no Interactive Settings command on the Tools menu.
	
	CAUSE
	=====
	
	These problems may occur as a result of one or both of the following
	situations:
	
	- If your computer has multiple user profiles, only the profile that is in use
	  when you ran Setup will run correctly. If you log in as someone else who has
	  a profile on your computer, you may experience these problems. For example,
	  if you log on to Windows NT version 3.51 as a user, Help may not run. But, if
	  you log on to Windows NT as the administrator, Help does run. In this case,
	  the Pptools.ppa file is not registered for the user account, but it is
	  registered for the administrator account because PowerPoint was installed
	  while you were logged on as administrator.
	
	- The Registry information for PowerPoint is incorrect or has become corrupted.
	  In this case, all users of your machine will receive the error.
	
	
	RESOLUTION
	==========
	
	Method 1: Update to PowerPoint 97
	---------------------------------
	
	PowerPoint 97 no longer writes these registry keys to the HKEY_CURRENT_USER
	branch. The keys are now written to the HKEY_LOCAL_MACHINE branch, this branch
	of the registry is available to all users of the computer.
	
	Method 2: Use the /y switch to re-register PowerPoint
	-----------------------------------------------------
	
	1. Log on to your computer using the user profile that exhibits the problems.
	
	2. Insert PowerPoint Disk 1 in drive A or B, or insert the PowerPoint compact
	  disc in the CD-ROM drive.
	
	3. Click the Windows Start button, and then click Run.
	
	4. In the Open box, type the following, and then click OK:
	
	  "<drive letter>:setup /y" (without the quotation marks)
	
	Setup will run but will not copy any files to your hard disk. It will simply
	update the registry.
	
	Method 3: Re-register PowerPoint
	--------------------------------
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it. If
	you are running Windows NT, you should also update your Emergency Repair Disk
	(ERD).
	
	If Method 2 for registering the program does not work, use this method to export
	keys related to PowerPoint, and then re-register the program.
	
	1. Click the Windows Start button, and then click Run.
	
	2. In the Open box, type the following, and then click OK:
	
	  "regedit" (without the quotation marks)
	
	3. Select the following registry key:
	
	     HKEY_CLASSES_ROOT\.ppt
	
	4. On the Registry menu, click Export Registry File.
	
	5. In the Save Registry File dialog box, type a file name for the registry key,
	  and then click Save.
	
	  When you return to the Registry Editor, the HKEY_CLASSES_ROOT\.ppt key is
	  still selected.
	
	6. On the Edit menu, click Delete. When you receive a message box asking you if
	  you want to delete this registry key, click Yes.
	
	7. Repeat steps 3 through 6 for the .pot, .pwz, and .pps keys.
	
	8. Start PowerPoint to reregister it.
	
	
	MORE INFORMATION
	================
	
	In Windows NT, separate user profiles are defined for each person that logs onto
	the computer. If Setup was run while you were logged on to a different profile,
	such as the Administrator profile, the registration information is stored with
	that profile instead of your profile. Separate registration information is
	stored for each profile, so if you log on using a different profile than the one
	you used when you installed the program, some components may not be accessible.
	
	Because PowerPoint stores most of its features and settings in the registry, all
	other users who log on to the computer are prevented from accessing those
	features. If the registry is corrupt or if the PowerPoint entries are invalid,
	the registry settings are inaccessible to PowerPoint, regardless of who is
	logged on.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This problem was corrected in Microsoft
	PowerPoint 97 for Windows.
	
	REFERENCES
	==========
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q128957 Optional Components Unavailable When User Profiles Are Enabled
	
	
	Additional query words: ppt7 ppt95 broken missing gone demo startup play lost function choice choose NT ppttools pptools1
	
	======================================================================
	Keywords          : kbsetup kbdta kbbuglist
	Technology        : kbPowerPtSearch kbPowerPt95 kbZNotKeyword2 kbPowerPt95Search
	Version           : WINDOWS:7.0
	Hardware          : x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
