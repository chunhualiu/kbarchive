---
layout: page
title: "Q190162: Terminal Server and the 2048 Open File Limitation"
permalink: /kb/190/Q190162/
---

## Q190162: Terminal Server and the 2048 Open File Limitation

{% raw %}

	Article: Q190162
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	To maintain compatibility with existing Server Message Block (SMB)-based
	products (for example, Microsoft Windows NT 3.x and 4.0, Microsoft Windows 95),
	Terminal Server's use of SMB has not been modified from Microsoft Windows NT
	Server 4.0. This can cause a problem if many Terminal Server users connect to a
	single network share, either on the Terminal Server or elsewhere on the network.
	The potential problem is an SMB limitation of 2048 open file handles.
	
	RESOLUTION
	==========
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	This behavior has been modified in SP4 to enable each Terminal Server client to
	maintain a separate virtual circuit. The new functionality is not enabled by
	default.
	
	To enable the new functionality, follow these steps:
	
	1. Ensure that the server is at or above SP4.
	
	2. From the server, run Registry Editor (Regedt32.exe).
	
	3. From the HKEY_LOCAL_MACHINE subtree, go to the following key:
	
	  \SYSTEM\CurrentControlSet\Services\Rdr\Parameters
	
	4. On the Edit menu, click Add Value.
	
	5. Add the following:
	
	  Value Name: MultipleUsersOnConnection
	  Data Type: REG_DWORD
	  Data: 0
	
	6. After you make this registry change, quit Registry Editor and restart the
	  server.
	
	MORE INFORMATION
	================
	
	Windows NT normally multiplexes all file requests sent to a single server over
	one virtual circuit. A locally unique identifier (LUID) and SessionID on
	Terminal Server sort user account credentials. These identifiers are used to
	receive credentials from the server for that user. Each request to access a
	specific file supplies this server credential handle. This enables multiple
	users on the workstation (really security contexts since Windows NT can have
	services access the network with different accounts) to share the virtual
	circuit and have their own security reflected on the server. This is known as
	User Level Security in SMB terminology.
	
	The SMB data structures reserve 11 bits for the file handle value. This reserve
	results in the 2048 files per connection situation. Terminal Server aggravates
	this problem, as many users may be simultaneously connecting from Terminal
	Server to the same share. It is therefore easier in Terminal Server to reach the
	file open limit than in Windows NT.
	
	Since the limitation is 2,048 open files per connection and all users use the
	same connection, a file-intensive program may be unsuccessful when the limit is
	reached. The Server Manager on the server that is hosting the share can display
	that the files are opened by the Terminal Server's computer name, since files
	are opened with a null user name even though security is checked through user
	name and credentials.
	
	Theoretically, a Terminal Server with 200 users simultaneously using the share
	would be limited to 10 open files per user.
	
	Regarding Windows 2000:
	-----------------------
	
	The MultipleUsersOnConnection registry value does not exist in Windows 2000
	because this is the behavior by default. The limit in Windows 2000 is 8192
	simultaneously open file handles per Terminal Server session.
	
	Regarding TSE4:
	---------------
	
	A 2048 simultaneously open file handles per Terminal Server; and with the TSE4
	MUX switch enabled, 2048 simultaneously open file handles per Terminal Server
	session.
	
	The preceding numbers only apply to the situation where a single Terminal Server
	has all users on that terminal server establishing SMB connections to a single
	file server. On Terminal Server, SMB is "smart" in the sense that if two users
	establish an SMB connection to the same file server, the SMB simply shares that
	connection. If another user establishes another SMB connection to a different
	file server, a new SMB connection is established to that file server.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTS400search kbNTTermServ400 kbNTTermServSearch
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
