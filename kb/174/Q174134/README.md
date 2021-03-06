---
layout: page
title: "Q174134: SMS: Exception 0E May Be Caused Unloading Remote Control Agent"
permalink: /kb/174/Q174134/
---

## Q174134: SMS: Exception 0E May Be Caused Unloading Remote Control Agent

{% raw %}

	Article: Q174134
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kbnetwork kbtshoot smsremtshoot kbRemoteProgkbbuglist
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information about how to do this, view the "Restoring
	the Registry" Help topic in Regedit.exe or the "Restoring a Registry Key"
	Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	If the Remote Control agent (Wuser.exe) is unloaded during an active Remote
	Control session, an exception 0E error may occur under Windows 95.
	
	CAUSE
	=====
	
	If the protocol used for Remote Control uses a NetBIOS interface, the symptom
	described above can occur, sometimes sporadically. When using Remote Control
	with NetBIOS over TCP/IP (NetBT), you will receive the following message:
	
	  An exception 0E occurred at xxx:xxxxxxxx in VxD VNBT(01)
	
	Although the message indicates that you may be able to continue normally, the
	current Windows 95 session must be stopped and then restarted.
	
	WORKAROUND
	==========
	
	To work around this problem, use a sockets-based transport for Remote Control.
	
	You can change the default Remote Control protocol on a per-client basis or on a
	site-wide basis. To change a client's Help Desk protocol from NetBIOS to either
	IP sockets or IPX sockets, you must modify the client's Sms.ini file. To do
	this, perform either of the sets of steps below, depending on if you want to
	perform the modification on a by-client or site-wide basis:
	
	Client-by-Client Basis
	----------------------
	
	1. Stop the Remote Control agent.
	
	2. Open the Sms.ini file in a text editor such as Notepad.
	
	3. Find the [SIGHT] section and locate the "Default Protocol=NetBIOS" line.
	
	4. Change this value from NetBIOS to either IP or IPX, depending on the network
	  protocol in use.
	
	Site-Wide Basis
	---------------
	
	To make all clients in this domain use IP sockets (except for client computers
	running Windows NT, which do this by default) or IPX sockets, you must make a
	registry change at the site server.
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall your operating system. Microsoft cannot guarantee that
	problems resulting from the incorrect use of Registry Editor can be solved. Use
	Registry Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	Information in the Registry" and "Edit Registry Data" Help topics in
	Regedt32.exe. Note that you should back up the registry before you edit it.
	
	To make the registry change, perform the following steps:
	
	1. Start Registry Editor (Regedt32.exe).
	
	2. Go to the following key in the registry:
	
	     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\Sites\<Sitecode>
	     \Domains\<Domain>
	
	3. Set the Default RC Protocol (REG_SZ) value to IP or IPX, depending on the
	  network protocol in use.
	
	This procedure forces all client computers running Windows 3.1, Windows for
	Workgroups, or Windows 95 that appear in this domain to use IP sockets as the
	default Remote Control protocol.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2. We are researching this problem and will post new information here
	in the Microsoft Knowledge Base as it becomes available.
	
	Additional query words: prodsms helpdesk
	
	======================================================================
	Keywords          : kbnetwork kbtshoot smsremtshoot kbRemoteProg kbbuglist
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
