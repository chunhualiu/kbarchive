---
layout: page
title: "Q179017: How to Migrate an Existing SNA Server to a New Hardware Platform"
permalink: /kb/179/Q179017/
---

## Q179017: How to Migrate an Existing SNA Server to a New Hardware Platform

{% raw %}

	Article: Q179017
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, 2.11 SP2, 3.0, 3.0 SP1, 3.0 SP2, 3.0 SP3, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	There may be occasions where it will be necessary to migrate your existing SNA
	Server configuration to a new computer, or to restore to an existing computer in
	the event it is rebuilt due to a hardware failure.
	
	MORE INFORMATION
	================
	
	NOTE: It is VERY IMPORTANT to keep a backup copy of your SNA configuration file
	in a place where it would be unaffected by a harware failure and in a place
	where it will not be accidentally deleted. Update the configuration EVERY time a
	modification is made. Without a valid current backup, complete restoration of
	the existing configuration is impossible.
	
	For more information on backup and restore of the configuration file, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q112636 Backup and Restore of COM.CFG
	
	This scenario assumes that the SNA Subdomain consists of only a single SNA server
	and it is properly configured as the Primary Configuration Server. This
	procedure would be used in the event of a computer replacement or a complete
	rebuild of an existing computer following a fatal hardware problem.
	
	1. Verify that you have a valid backup of your configuration file.
	
	2. Use the Snacfg.exe utility to have a text copy printed to be used in steps 5
	  and 7.
	
	3. Remove server from the network physically by shutting the computer off. Then
	  remove the server's machine account in the Windows NT Domain using Server
	  manager.
	
	4. Install Windows NT Server along with current Service Pack levels. Add the
	  computer to the Windows NT domain with the same machine name as the original.
	  Also verify that the same LAN transport protocols are installed. If using
	  TCP/IP, make sure that the proper IP address is assigned.
	
	5. Install SNA Server. Make sure that proper Link Services are installed. These
	  would normally be the same Link Services that were installed previously
	  unless the server to host physical connection has been changed. For example,
	  a Token Ring card was replaced by Ethernet.
	
	6. Restore the SNA Configuration from backup file.
	
	7. Make sure that connections are configured with the proper Link Service.
	
	8. After verifying proper operation, update SNA Server to the Service Pack level
	  that was installed previously, or to the latest Service Pack if a newer one
	  is available.
	
	9. Backup configuration file in a place where it would be unaffected by a
	  harware failure and in a place where it will not be accidentally deleted.
	
	Additional query words: snafaq
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ211 kbSNAServ400 kbSNAServ211SP1 kbSNAServ211SP2 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1,3.0 SP2,3.0 SP3,4.0
	Hardware          : x86
	Issue type        : kbhowto kbinfo
	
	=============================================================================
	

{% endraw %}
