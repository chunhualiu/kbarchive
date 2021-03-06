---
layout: page
title: "Q311462: SMS: User or User Group Advertisements Do Not Run Immediately"
permalink: /kb/311/Q311462/
---

## Q311462: SMS: User or User Group Advertisements Do Not Run Immediately

{% raw %}

	Article: Q311462
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Operating System(s): 
	Keyword(s): kbClient kbsms200bug kbsms200fix kbSoftwareDist
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Mandatory user-based or user group-based advertisements may not run immediately
	after a user logs on. Depending on the "Refresh interval" value that is defined
	by the Systems Management Server (SMS) administrator, it may take several
	minutes for advertisement to be offered to a user. Additionally, if the
	advertisement is configured to run when the user logs on, the advertisement
	might not run until the user logs on for the second time.
	
	CAUSE
	=====
	
	Advertised Program Monitor (Smsmon32.exe) starts the Offer data providers when a
	user logs on only if that user has previously defined a custom "Refresh
	interval" value for the Offer data providers that is different from the value
	that is defined in the system-wide site settings.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem that is described in this article. Only apply it to systems
	that are experiencing this specific problem. This fix may receive additional
	testing. Therefore, if you are not severely affected by this problem, Microsoft
	recommends that you wait for the next Systems Management Server service pack
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, visit the following Microsoft
	Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are ordinarily incurred for support calls
	may be canceled if a Microsoft Support Professional determines that a specific
	update will resolve your problem. The usual support costs will apply to
	additional support questions and issues that do not qualify for the specific
	update in question.
	
	The English post-Service Pack 3 (SP3) version of this fix should have the
	following file attributes or later:
	
	  
	
	  Date         Time   Version        Size       File name     Platform
	  --------------------------------------------------------------------
	  01-Mar-2001  22:35  2.0.92.9         654,485  Apasetup.exe     Alpha
	  01-Mar-2001  22:20  2.0.1493.3216    293,648  Ccim32.dll       Alpha
	  01-Mar-2001  22:35  2.0.92.9       1,925,226  Ccmcore.exe      Alpha
	  01-Mar-2001  22:35  2.0.1493.3219  1,938,704  Clibase.dll      Alpha
	  01-Mar-2001  22:35  2.0.1493.3219  4,441,921  Clicore.exe      Alpha
	  01-Mar-2001  22:20  2.0.1493.3216    125,712  Clisvcl.exe      Alpha
	  01-Mar-2001  22:35  2.0.1493.3219     13,584  Cliver.exe       Alpha
	  01-Mar-2001  22:20  2.0.1493.3216     66,832  Cqmgr32.dll      Alpha
	  01-Mar-2001  13:00  2.0.1493.3125    578,832  Mslmclin.dll     Alpha
	  01-Mar-2001  22:20  2.0.1493.3216     73,488  Odpsys32.exe     Alpha
	  01-Mar-2001  22:20  2.0.1493.3216     82,192  Odpusr32.exe     Alpha
	  01-Mar-2001  22:35  2.0.1493.3219    382,224  Smsapm32.exe     Alpha
	  01-Mar-2001  22:20  2.0.92.9         691,596  Swdist32.exe     Alpha
	  01-Mar-2001  22:35  2.0.92.9         394,054  Apasetup.exe     I386
	  01-Mar-2001  13:00  2.0.1493.3125    259,936  Bindclin.dll     I386
	  01-Mar-2001  22:20  2.0.1493.3216    181,584  Ccim32.dll       I386
	  01-Mar-2001  22:35  2.0.92.9       1,324,070  Ccmcore.exe      I386
	  01-Mar-2001  22:35  2.0.1493.3219  1,223,584  Clibase.dll      I386
	  01-Mar-2001  22:35  2.0.1493.3219  3,401,549  Clicore.exe      I386
	  01-Mar-2001  22:20  2.0.1493.3216     88,432  Clisvcl.exe      I386
	  01-Mar-2001  22:35  2.0.1493.3219      8,512  Cliver.exe       I386
	  01-Mar-2001  22:20  2.0.1493.3216     39,264  Cqmgr32.dll      I386
	  01-Mar-2001  13:00  2.0.1493.3125    338,272  Mslmclin.dll     I386
	  01-Mar-2001  13:00  2.0.1493.3125    269,664  Ndsclin.dll      I386
	  01-Mar-2001  22:20  2.0.1493.3216     53,104  Odpsys32.exe     I386
	  01-Mar-2001  22:20  2.0.1493.3216     59,248  Odpusr32.exe     I386
	  01-Mar-2001  22:35  2.0.1493.3219    287,088  Smsapm32.exe     I386
	  01-Mar-2001  22:20  2.0.92.9         637,723  Swdist32.exe     I386
	  01-Mar-2001  22:35                        67  Compverbase.ini
	  01-Mar-2001  22:35                        67  Compversmsapm32.ini
	  01-Mar-2001  22:35                        67  Compverswdist.ini
	
	NOTE: Because of file dependencies, the most recent hotfix or feature that
	contains the above files may also contain additional files.
	
	
	
	WORKAROUND
	==========
	
	To work around this problem, you can define a custom refresh interval in
	Advertised Programs Monitor, or you can run the CLIUTILS.EXE /Start "WNET User
	Groups Offer Data Provider" command in the user's logon script (or by some other
	automated method), to force the Offer data provider to start when a user logs
	on.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	the Systems Management Server 2.0 Service Pack 4 Hotfix Rollup Package (HRP).
	
	For additional information about the SMS 2.0 SP4 HRP, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q323206 SMS: List of Bugs Fixed in the Systems Management Server 2.0 SP4 HRP
	
	MORE INFORMATION
	================
	
	How to Install the Hotfix
	-------------------------
	
	How to Use the Hotfix Installer:
	
	NOTE: You can use this method only on Intel-based computers.
	
	1. Copy the hotfix folder structure to a share on your network. Note that
	  Q311462.exe is a Microsoft SMS Installer file that updates specific files on
	  your site server.
	
	2. Log on to the site server by using an account with administrative
	  permissions.
	
	3. On the site server, quit the SMS Administrator console.
	
	4. Run the Q311462.exe tool and then follow the instructions in the wizard. You
	  can run the file in Quiet mode by using the /s switch.
	
	How to Install the Hotfix Manually:
	
	1. Stop the SMS_EXECUTIVE and the SMS_SITE_COMPONENT_MANAGER services.
	
	2. Replace the Clicore.exe and Ccmcore.exe files in the
	  <Sms_root>\Inboxes\Clicomp.src\Base\<Platform> folder with the
	  version from the hotfix.
	
	3. Replace the Apasetup.exe file in the
	  <Sms_root>\Inboxes\Clicomp.src\smsapm32\<Platform> folder with
	  the version from the hotfix.
	
	4. Replace the Swdist32.exe file in the
	  <Sms_root>\Inboxes\Clicomp.src\SWDist\<Platform> folder with the
	  version from the hotfix.
	
	5. Replace the Compver.ini file in the <Sms_root>\Inboxes\Clicomp.src\Base
	  folder with the Compverbase.ini file from the hotfix. Rename the
	  Compverbase.ini file to Compver.ini when you do this.
	
	6. Replace the Compver.ini file in the
	  <Sms_root>\Inboxes\Clicomp.src\smsapm32 folder with the
	  Compversmsapm32.ini file from the hotfix. Rename the Compversmsapm32.ini file
	  to Compver.ini when you do this.
	
	7. Replace the Compver.ini file in the
	  <Sms_root>\Inboxes\Clicomp.src\swdist folder with the Compverswdist.ini
	  file from the hotfix. Rename the Compverswdist.ini file to Compver.ini when
	  you do this.
	
	8. Replace the following files in the <Sms_root>\Bin\<Platform>
	  folder with the versions from the hotfix:
	
	  Bindclin.dll
	  Ccim32.dll
	  Clisvcl.exe
	  Cqmgr32.dll
	  Mslmclin.dll
	  Ndsclin.dll
	  Odpsys32.exe
	  Odpusr32.exe
	  Smsapm32.exe
	
	9. Restart the SMS_EXECUTIVE and the SMS_SITE_COMPONENT_MANAGER services. Let
	  the updated Compver.ini, Clicore.exe, and Ccmcore.exe files be propagated to
	  all logon points and client access points in the site.
	
	Additional query words: prodsms user group logon mandatory
	
	======================================================================
	Keywords          : kbClient kbsms200bug kbsms200fix kbSoftwareDist 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
