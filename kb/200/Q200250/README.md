---
layout: page
title: "Q200250: XFOR: Importing .sc2 File into Outlook After Migration"
permalink: /kb/200/Q200250/
---

## Q200250: XFOR: Importing .sc2 File into Outlook After Migration

{% raw %}

	Article: Q200250
	Product(s): Microsoft Exchange
	Version(s): WINDOWS:97; winnt:5.5
	Operating System(s): 
	Keyword(s): exc55
	Last Modified: 27-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	- Microsoft Outlook 97 
	- Microsoft Outlook 98 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	After the Exchange Migration Wizard has converted Microsoft Mail, GroupWise,
	PROFS, or other third-party server accounts into Exchange Server accounts, it
	converts each account's Microsoft Schedule+ or Calendar data into .sc2 format
	and e-mails them as attachments to the new e-mail account on the Exchange Server
	computer.
	
	This article explains the different procedures that take place when the schedule
	information is automatically or manually migrated.
	
	MORE INFORMATION
	================
	
	When the user double-clicks the .sc2 attachment in the message, the file
	contents are imported into Outlook as Calendar items.
	
	The following is the text of the e-mail message automatically sent to the user.
	
	  The attached file is a copy of your migrated calendar information. If you
	  imported your calendar automatically when you first logged on, you do not
	  need to continue. Verify that your calendar information was imported
	  correctly, and then delete this message.
	
	NOTE: The Standard or Full installation of Outlook 98 automatically installs the
	Schedule+ support component necessary to convert the .sc2 file.
	
	To Manually Import Calendar Information
	---------------------------------------
	
	If you migrated calendar information to a personal folder file (.pst) or were not
	prompted to import your calendar information automatically, you can import it
	manually. Use the appropriate steps for your client platform.
	
	Outlook
	-------
	
	1. On the File menu, click Save Attachments.
	
	2. Type the location and file name for the attached file, and then click Save.
	
	3. On the File menu, click Import and Export.
	
	4. Click " Import from another program or file", and then click Next.
	
	5. If the file attachment is a .cal file, click Schedule+ 1.0.
	  If the file attachment is an .scd file, click Schedule+ 7.0.
	  If the file attachment is an .sc2 file, click Schedule Plus Interchange.
	
	6. Type the path and file name of the file you want to import. Under Options,
	  click "Do not import duplicate items", to ensure that any previously imported
	  items are not duplicated.
	
	7. Type the password for the calendar file, and then click OK.
	
	8. Click Finish to complete the calendar migration.
	
	Outlook Calendar for Windows for Workgroups Version 3.11 and Windows Version 3.1
	--------------------------------------------------------------------------------
	
	If you migrated calendar information to the Exchange Server information store,
	your calendar is automatically migrated, and you do not need to continue. Verify
	that your calendar information was imported correctly, and then delete this
	message.
	
	If you migrated calendar information to a personal folder file (.pst) or your
	calendar information was not imported correctly, you can import it manually.
	
	1. On the calendar message, on the File menu, click Save As.
	
	2. Click Attachments, type the location and file name, and then click OK.
	
	3. If the file you want to import is Schedule Plus Interchange (.sc2) file, go
	  to step 9. If the file you want to import is a Schedule+ 1.0 (.cal) file, or
	  a Schedule+ 7.0 (.scd) file, start the Outlook Calendar by clicking the Show
	  Calendar toolbar button in Outlook, or running Outlook Calendar from the
	  group where it is installed.
	
	4. On the main Outlook Calendar menu, click File, click Open, and then click
	  "Archive or Project Schedule".
	
	5. Select the file to open by typing the path and file name that you specified
	  in step 2, and then click OK.
	
	6. In this new Outlook Calendar window, on the File menu, click Export, and then
	  click Outlook Calendar Interchange.
	
	7. Select a location and file name for the export file (.sc2), and then click
	  OK.
	
	8. Close the Outlook Calendar window.
	
	9. On the main Outlook Calendar menu, click File, click Import, and then click
	  Outlook Calendar Interchange.
	
	10. Select the file to import by typing the path to the .sc2 file, and then
	  click OK. The calendar data from the .sc2 file will be imported to your
	  Outlook Calendar.
	
	Event ID 4088 is written to the application event log on the Migration Wizard
	server.
	
	With Outlook 8.03, you can also use the .sc2 file converter utility (Impsc2.exe).
	Install the .sc2 file converter utility on the client computer by running
	Msimpsc2.exe from the Outlook 8.03 compact disc.
	
	Impsc2.exe can also be used from the command-line
	
	  
	
	  Impsc2 <file name>.sc2
	
	  where <file name> is the file you want to import.
	
	NOTE: Impsc2.exe uses OLE automation to the Outlook client. Therefore, the
	utility should work with all versions of Outlook. However, the utility works
	most reliably with the Outlook 8.03 client since each version of Outlook (8.01,
	8.02, 8.03) includes some fixes in OLE automation.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 
	Technology        : kbOutlookSearch kbExchangeSearch kbExchange550 kbZNotKeyword2 kbOutlook97Search kbOutlook98Search kbZNotKeyword3
	Version           : WINDOWS:97; winnt:5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
