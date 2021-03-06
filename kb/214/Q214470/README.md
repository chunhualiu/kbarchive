---
layout: page
title: "Q214470: How to Move the Location of a Locally Cached Profile"
permalink: /kb/214/Q214470/
---

## Q214470: How to Move the Location of a Locally Cached Profile

{% raw %}

	Article: Q214470
	Product(s): Microsoft Windows NT
	Version(s): WINDOWS:2000; winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows 2000 Server 
	- Microsoft Windows 2000 Professional 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SUMMARY
	=======
	
	By default, the locally cached copy of a profile is stored in
	%SystemRoot%\Profiles\, which may be an issue if you have a large number of
	people logging on to a computer. If you have a large number of people logging on
	to a computer (which creates a large number of profiles), disk space on the
	operating system partition may become scarce. You can move the locally cached
	copy of a profile to another local partition.
	
	MORE INFORMATION
	================
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To move the locally cached copy of the profile, you will need to know the
	security identifier (SID) of the user whose profile you want to move. You can
	identify the SID by using GetSID.exe from the Windows NT Server 4.0 Resource
	Kit.
	
	Windows NT 4.0 stores the local profile information in the registry under the
	following key:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList
	
	Under the ProfileList key, there will be subkeys named with the SIDs of the users
	who have logged on to this computer. (To find the profile information for the
	user whose locally cached profile you want to move, find the SID for the user
	with the GetSID.exe utility.) Inside of the appropriate user's subkey, you will
	see a string value named ProfileImagePath. ProfileImagePath should be set to a
	local path where you want to store the profile.
	
	If you do not have a roaming profile and you want to maintain your profile after
	you change the locally cached profile path, copy the contents of your old
	locally cached profile folder to the new location set in the ProfileImagePath
	value.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbwin2000Serv kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbwin2000ServSearch kbwin2000Search kbwin2000ProSearch kbwin2000Pro kbNTTermServ400 kbNTTermServSearch
	Version           : WINDOWS:2000; winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
