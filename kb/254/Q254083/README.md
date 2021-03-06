---
layout: page
title: "Q254083: SMS 2.0 SP1 Is Not Compatible with WMI Version 1085"
permalink: /kb/254/Q254083/
---

## Q254083: SMS 2.0 SP1 Is Not Compatible with WMI Version 1085

{% raw %}

	Article: Q254083
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:2.0,2.0 SP1
	Operating System(s): 
	Keyword(s): kbsms200 kbsms120 kbsms120bug
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you 
	modify the registry, make sure to back it up and make sure that you understand how to restore 
	the registry if a problem occurs. For information about how to back up, restore, and edit the 
	registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	After you upgrade to version 1085 of Windows Management Instrumentation (WMI) on
	the Systems Management Server (SMS) site provider site system, the SMS
	Administrator console can no longer connect to the site database. Instead, the
	following error message may be generated:
	
	  Runtime Error!
	  Program C:\winnt\system32\mmc.exe
	  abnormal program termination
	
	CAUSE
	=====
	
	This behavior is caused by security changes in the later WMI version that
	prevents the SMS provider from functioning correctly.
	
	WORKAROUND
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To restore functionality to a site server that has been upgraded, remove WMI and
	install the version that is included with SMS.
	
	NOTE: Removing WMI removes all data and provider registrations from the
	repository. Instructions for restoring the data and registrations that SMS
	depends on are listed later in this article. For instructions regarding the
	restoration of third-party software products that are also dependant on WMI,
	please contact the product manufacturer.
	
	Manual Removal of WMI
	---------------------
	
	1. Stop the Windows Management service.
	
	2. Using the Instsrv.exe utility from the Microsoft Windows NT Resource Kit,
	  remove the service by using a command syntax similar to:
	
	  instsrv winmgmt remove
	
	Note that this command syntax may vary depending on the installed build number.
	
	3. Manually delete the %SystemRoot%\System32\Wbem folder and its contents.
	
	4. In the registry, remove the WBEM key from:
	
	  HKEY_LOCAL_MACHINE\Software\Microsoft
	
	Reinstallation of WMI
	---------------------
	
	1. Set up the Windows Management Instrumentation (WMI) server components. At a
	  command prompt, in the <Drive>:\<Sms_root>\Bin\<Platform>
	  folder, type the following command by using the hotfixed version of
	  Wbemsdk.exe:
	
	  wbemsdk.exe /s /server
	
	2. To restore the provider and other data needed by the site, manually compile
	  the MOF files by typing the following commands at a command prompt, pressing
	  ENTER after each command:
	
	  cd %systemroot%\system32\wbem
	  mofcomp x:\<sms_root>\bin<\platform\>sms_schm.mof
	  mofcomp x:\<sms_root>\bin<\platform\>smsprov.mof
	  mofcomp x:\<sms_root>\bin<\platform\>cmprov.mof
	  mofcomp x:\<sms_root>\bin<\platform\>cpprov.mof
	  mofcomp x:\<sms_root>\bin<\platform\>pollprov.mof
	  mofcomp x:\<sms_root>\bin<\platform\>netdisc.mof
	
	If the SMS provider is located on a computer other than the site server, compile
	the .mof files located on that computer by typing the following lines at a
	command prompt
	
	  cd %systemroot%\system32\wbem
	  mofcomp <x>:\smsprov\mofs\<sitecode>\sms_schm.mof
	  mofcomp <x>:\smsprov\mofs\<sitecode>\smsprov.mof
	
	where <x> is the drive where the provider is installed.
	
	3. In the Systems Management Server Administrator console, the node under the
	  Systems Management Server node may state that the connection did not succeed.
	  If so, delete that connection node by right-clicking it and then clicking
	  Delete. Restore the node by right-clicking the Systems Management Server
	  node, pointing to All Tasks, and then clicking Connect To Site Database. In
	  the Site Database Connection Wizard, click Next, and then click "Reconnect to
	  the site database for this site server". Click Next, and then click Finish.
	
	4. Restart the computer.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	WMI version 1085 is automatically installed by several third-party products that
	may have dependencies on using the newer version of WMI. These products should
	not be installed on an SMS 2.0 or 2.0 SP1 site server or provider server.
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1
	Version           : winnt:2.0,2.0 SP1
	Issue type        : kbprb
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
