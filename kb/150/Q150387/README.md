---
layout: page
title: "Q150387: Only 5 Users Can Connect to Evaluation Copy of NT Server"
permalink: /kb/150/Q150387/
---

## Q150387: Only 5 Users Can Connect to Evaluation Copy of NT Server

{% raw %}

	Article: Q150387
	Product(s): Microsoft Windows NT
	Version(s): 3.51,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Only five users can connect to the resources of a Windows NT Server.
	
	CAUSE
	=====
	
	You may be using the MSDN version of Windows NT Server, which is designed for
	software developers who want to design and test software products that operate
	on the BackOffice platform. By design, the MSDN version of Windows NT Server
	allows only five simultaneous connections by an unlimited number of users to any
	of the services provided by the Server.
	
	MORE INFORMATION
	================
	
	Use one the following methods to determine whether your currently installed
	version of Windows NT Server is the MSDN version:
	
	- Check the label. MSDN has a different product identification. The compact
	  disc envelope is labeled "BackOffice Test Platform" [ASCII 133]
	
	- Read the licensing configuration, displayed during Setup. It includes the
	  following notice:
	
	  This is a special version of Windows NT Server for the BackOffice Test
	  Platform. This version supports up to 5 concurrent users for testing and
	  development purposes.
	
	  The connection limits cannot be changed; if this limit does not meet your
	  needs, you should consider purchasing the retail version of Windows NT Server
	  with the appropriate number of client licenses.
	
	Once Windows NT Server is running, you can use the following method to determine
	if you are using the MSDN version:
	
	- Double-click on the License icon in Control Panel. The following message
	  appears:
	
	  Not available in MSDN Edition of BackOffice
	
	
	The five-user limitation is explained in the following sections of the MSDN
	License agreement:
	
	2.  GRANT OF LICENSE:
	---------------------
	
	(b) Use-Server Software:
	You may use the Server Software for the sole purposes of designing, developing,
	and testing your software product(s) that are designed to operate in conjunction
	with Microsoft BackOffice. The server Software may not be used to support the
	designing, development and testing of software product(s) (e.g., as a repository
	for source code). The components of the Server Software may only be used on one
	and the same Server. A maximum of five (5) simultaneous connections by an
	unlimited number of users may be made to access and use the services provided by
	the Server.
	
	In other words, the software is provided so that customers can adequately test
	their software on the BackOffice platform, but it is not to be used as their
	development platform. They have to buy retail software to use software as their
	development base for tools.
	
	10.  DESCRIPTION OF OTHER RIGHTS AND LIMITATIONS:
	-------------------------------------------------
	
	No Production Use: The SOFTWARE PRODUCT may only be used for development purposes
	as described in Section 1. The SOFTWARE PRODUCT may not be used in a production
	environment.
	
	(a) No Commercial Use: You may not use the Server Software as part of or as the
	basis for a commercial public access data network that consists of two or more
	servers and that carries end-to-end electronic information traffic, such as
	messaging, data replication, fax, EDI, or telex, unless you obtain a separate
	commercial use license from Microsoft.
	
	
	Additional query words: prodnt eval resale evaluation
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS351search
	Version           : :3.51,4.0
	
	=============================================================================
	

{% endraw %}
