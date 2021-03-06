---
layout: page
title: "Q322810: Windows Services For UNIX Impaired After Windows 2000 Upgrade"
permalink: /kb/322/Q322810/
---

## Q322810: Windows Services For UNIX Impaired After Windows 2000 Upgrade

{% raw %}

	Article: Q322810
	Product(s): Microsoft Windows NT
	Version(s): 3.0
	Operating System(s): 
	Keyword(s): kbtool
	Last Modified: 03-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Services for UNIX, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you upgrade your computer from Microsoft Windows NT 4.0 to Microsoft
	Windows 2000, certain Windows Services For UNIX 3.0 components no longer
	function optimally.
	
	RESOLUTION
	==========
	
	To resolve this issue, remove and then reinstall these components to replace the
	Windows NT 4.0-specific components with Windows 2000-specific Windows Services
	For UNIX components. Use the Add/Remove Programs tool in Control Panel to remove
	the following components if they are installed on the system:
	
	  Client for NFS
	  Gateway For NFS
	  Telnet Server
	
	After you have removed these components, use Add/Remove Programs to reinstall
	these components. This method will upgrade the services to the Windows
	2000-specific components.
	
	NOTE: If you run the Installation Wizard and select Reinstall/Repair, this method
	does not upgrade these components.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	The Windows NT 4.0 Windows Services For UNIX binaries listed in the "Resolution"
	section of this article will run on either Windows NT 4.0 or Windows 2000-based
	systems. However, Microsoft recommends that you individually upgrade these
	components after you upgrade to Windows 2000. Windows 2000 supports the /robust
	switch. This flag tells the Microsoft Interface Definition Language (MIDL)
	compiler to generate additional error-checking information, which the Network
	Data Representation (NDR) engine uses to perform integrity checks at run time.
	The /robust switch is available only under Windows 2000. These components were
	compiled by using the /robust switch.
	
	For more information about /robust, MIDL, and NDR, visit the following Microsoft
	Web site:
	
	  http://msdn.microsoft.com/default.asp (http://msdn.microsoft.com/default.asp)
	
	Additional query words: solar coaster solarcoaster interix
	
	======================================================================
	Keywords          : kbtool 
	Technology        : kbWinServiceUNIXSearch kbWinServiceUNIX300
	Version           : :3.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
