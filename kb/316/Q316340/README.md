---
layout: page
title: "Q316340: HOW TO: Back Up Files and Folders on a  Computer in Windows NT"
permalink: /kb/316/Q316340/
---

## Q316340: HOW TO: Back Up Files and Folders on a  Computer in Windows NT

{% raw %}

	Article: Q316340
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbtool kbAudITPro kbHOWTOmaster
	Last Modified: 09-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Requirements
	- Backing Up Files and Folders on a Windows NT 4.0 Computer
	
	- REFERENCES
	
	SUMMARY
	=======
	
	This step-by-step article describes how to back up files and folders on a
	Windows NT Server 4.0-based or Windows NT Workstation 4.0-based computer. After
	you have backed up your data, you can restore it from tape.
	
	Requirements
	------------
	
	- A computer (that meets the requirements that are listed on the appropriate
	  Hardware Compatibility List) on which Windows NT Server 4.0 or Windows NT
	  Workstation 4.0 is installed.
	- A tape drive (that meets the requirements that are listed on the appropriate
	  Hardware Compatibility List) must be installed in the computer, and a tape
	  must be inserted in the drive.
	
	Backing Up Files and Folders on a Windows NT 4.0 Computer
	---------------------------------------------------------
	
	Tape backup is an important part of a network's fault-tolerance plan. You can use
	Windows NT Backup to back up files and folders on a Windows NT 4.0-based
	computer, both locally and across the network. If you want to back up remote
	files, you must first connect to a shared folder on the server where the remote
	files are located.
	
	NOTE: Windows NT Backup can only back up the Registry or event logs on the
	Windows NT 4.0-based computer on which the tape drive is installed.
	
	Because Windows NT Backup does not back up files that are locked open by
	programs, you should notify users to close files before you start the backup
	job. Or, you can start the backup job at a time when users do not have access to
	files, such as after business hours.
	
	To back up files and folders, you need to either be a member of the
	administrators, backup operators, or server operators groups, or you must have
	the "Back up files and directories" user right. To back up files and folders:
	
	1. Click Start, point to Programs, point to Administrative Tools (Common), and
	  then click Backup.
	
	2. In the Backup dialog box, click Drives on the Window menu.
	
	3. If you want to back up an entire drive or drives, click to select the check
	  boxes next to the drives you want to back up. If you want to back up specific
	  files or folders on a drive, double-click the drive to expand it. Then
	  continue to expand folders until the files or folders you want to back up are
	  displayed. Next, click to select the check box next to each file and folder
	  you want to back up. If you then want to select files on another drive, click
	  Drives on the Window menu, and then expand the drive and click to select the
	  check box next to each file and folder you want to back up. When you have
	  finished selecting files and folders to be backed up, click Backup.
	
	4. In the Backup Information dialog box, type a name for the tape in the Tape
	  Name box. In the Description box, type a description of the backup. Select
	  the backup type you want to use, and then select the backup options you want
	  to use for this backup.
	
	  NOTE: If you select the Verify After Backup option, the amount of time that is
	  needed for the backup is approximately doubled.
	
	  After you have configured all of the tape and backup options, click OK. If a
	  Replace Information dialog box is displayed, click Yes to overwrite the
	  existing data on the tape.
	
	5. Windows NT Backup backs up the selected data. When the backup is complete,
	  click OK in the Backup Status dialog box. Quit Windows NT Backup to complete
	  the process of making a backup on your Windows NT 4.0-based computer.
	
	REFERENCES
	==========
	
	For more information about how to back up and restore files and folders on a
	Windows NT 4.0-based computer, see Module 11 of the Microsoft Official
	Curriculum, Course Number 803, Administering Microsoft Windows NT 4.0:
	
	  http://www.microsoft.com/TRAINCERT/SYLLABI/803BFINAL.ASP
	
	For additional information about how to restore data from tape, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q309340 HOW TO: Use Backup to Restore Files and Folders on Your Computer
	
	For additional information about how to schedule a backup job, click the article
	number below to view the article in the Microsoft Knowledge Base:
	
	  Q313289 HOW TO: Use the At.exe Command to Schedule a Backup on a Windows NT
	  4.0-Based Computer
	
	Additional query words:
	
	======================================================================
	Keywords          : kbtool kbAudITPro kbHOWTOmaster 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
