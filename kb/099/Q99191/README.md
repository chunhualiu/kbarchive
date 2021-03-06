---
layout: page
title: "Q99191: Logon to File Server with Boot Disk"
permalink: /kb/099/Q99191/
---

## Q99191: Logon to File Server with Boot Disk

{% raw %}

	Article: Q99191
	Product(s): Microsoft LAN Manager
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	SUMMARY
	=======
	
	Sometimes, attempting to connect to a file server with user level security with
	a basic boot disk returns the message: "Connection Refused or Syntax Error".
	
	MORE INFORMATION
	================
	
	Here is how to remove this condition:
	
	1. Create a boot disk.
	
	Format a floppy disk with system on it. Run ndisk/f from your ninstall directory
	to create a basic bootdisk. The server copies all the necessary files to the
	floppy disk
	
	1. Use the disk you just created to boot your workstation.
	
	2. After boot up, net start your workstation. Type: "net start wksname" (without
	  the quotation marks) [enter]. Wksname can be your user id.
	
	NOTE: If your user id has user or admin. rights and a password, you must put an
	asterisk with your net use. If you don't, you get the error: Connection refused
	or syntax error.
	
	1. Type: "Net use k: \\srvname\sharename *" (without the quotation marks)
	  [enter].
	
	This prompts you for a password.
	
	1. If you don't have a password for the wksname you put in, you are logged in
	  with the privileges assigned to that account.
	
	2. If your user id doesn't have a password, and you delete or disable your guest
	  account, you get the error: access denied.
	
	Here is an example of autoexec.bat:
	
	@echo off
	set path=\LANMAN\basic
	c:\LANMAN\drivers\protocol\netbeui\netbeui.exe
	c:\LANMAN\basic\netbind
	net start workstation admin
	net use k: \\server1\c$ *
	
	Additional query words: 2.0 2.1 2.1A 2.2 boot
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	

{% endraw %}
