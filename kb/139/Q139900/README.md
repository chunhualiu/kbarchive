---
layout: page
title: "Q139900: Using Intel NetportExpress XL Print Server with Windows NT"
permalink: /kb/139/Q139900/
---

## Q139900: Using Intel NetportExpress XL Print Server with Windows NT

{% raw %}

	Article: Q139900
	Product(s): Microsoft Windows NT
	Version(s): 3.1 3.5 3.51 4.0
	Operating System(s): 
	Keyword(s): kbprint kbPrinting
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Advanced Server, version 3.1 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you migrate from a Novell Network to a Microsoft Network, you may have
	difficulty getting your Intel NetPortExpress XL print server to service print
	request, even if the Windows NT server is running File and Print Services for
	Netware (FPNW).
	
	MORE INFORMATION
	================
	
	An Intel NetportExpress XL on a Novell Network is generally configured to use
	IPX/SPX. To use this print server on a Microsoft Network, it must be configured
	to support NetBIOS.
	
	NOTE: For the NetportExpress XL to work on the Microsoft Network, the Application
	Code and RBL code must be version 3.04 or later.
	
	For detailed information contact Intel FaxBack service at (800) 525-3019 and
	request Document 6072, or Intel technical support at (503) 264-7000.
	
	After upgrading the NetPort software, you must configure the Windows NT server:
	
	1. Create a user account and directory for the NETPORT.
	
	2. Insure the Password is blank and that the "User Must Change Password at Next
	  Logon" is NOT selected.
	
	3. The account name should be NETPORT and the Shared directory should be
	  NETPORT.
	
	4. The NETPORT user account needs Read-Only access to the directory \NETPORT.
	
	Now, install the NETPORT Manager software. It can be installed on a workstation
	as well as the server. Follow the instructions on the disk. This is the software
	for configuring all of the NETPORT print servers.
	
	Complete the following steps for configuring the Netport with Netport Manager:
	
	1. Start Netport Manager and select a NetportExpress print server from the list.
	  Choose Configure.
	
	NOTE: The NetBEUI protocol is required to initialize the Intel NetportExpress
	Print Server hardware if you are installing on a Microsoft network.
	
	2. If you are prompted, fill in the Set Remote Boot Load Servers window: If
	  there are buttons for Server Type, select NetBIOS. Select a domain from the
	  list, or type one in. Select a shared directory to connect to from the list,
	  or type one in. The name must be in the form:
	
	  \\<server_name>\<share_name>
	
	  This should be the same as the user name of the account created on the Windows
	  NT server. Choose OK.
	
	  NOTE: There may be a delay while the NetportExpress updates its RBL
	  information.
	
	3. Choose Protocols, select Windows NT, Choose Configure (this is not available
	  prior to version 3.04)
	
	4. Fill in the "Configure Microsoft...Print Server Window". Choose Use Defaults
	  to accept the default choices or select a domain for print services from the
	  list (or type one in). For each port, enter a name and description.
	
	5. If you want to use IP, Choose Set IP Address. Either select "Dynamically
	  Configure" (requires DHCP), or fill the correct IP address information. Exit
	  Netport Manager.
	
	6. Now you can start Print Manager to create the printer. Make sure the share
	  name is the same as the printer name.
	
	The NetportExpress XL is manufactured by Intel, a vendor independent of
	Microsoft; we make no warranty, implied or otherwise, regarding this product's
	performance or reliability.
	
	Additional query words: prodnt netport express
	======================================================================
	Keywords          : kbprint kbPrinting 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNTS351search kbWinNTS350search kbWinNT310Search
	Version           : 3.1 3.5 3.51 4.0
	
	=============================================================================
	

{% endraw %}
