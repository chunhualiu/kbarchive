---
layout: page
title: "Q129785: PC Win: Err Msg: ...MAILSPL Caused a GPF in Module MAILSPL.EXE"
permalink: /kb/129/Q129785/
---

## Q129785: PC Win: Err Msg: ...MAILSPL Caused a GPF in Module MAILSPL.EXE

{% raw %}

	Article: Q129785
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.0b,3.2,3.2a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for Windows, versions 3.0b, 3.2, 3.2a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use version 3.0b, 3.2, or 3.2a of Microsoft Mail for Windows, and you
	double-click the Microsoft Mail icon from Windows and enter a mailbox id and
	password, the following error message, or a similar General Protection Fault
	(GP-Fault) message, may occur:
	
	  Application error: MAILSPL caused a GPF in module MAILSPL.EXE at XXXX:XXXX."
	
	CAUSE
	=====
	
	In most cases, the problem is a corrupt MMF (Mail Message File) that is located
	on the Mail database under the MMF subdirectory (HEX-ID.MMF) or on the local
	hard drive (USERNAME.MMF).
	
	RESOLUTION
	==========
	
	To check and see if the MMF is corrupt, log out of mail, rename the MMF file on
	the server (or local drive), and log back in to Mail; this will create a new MMF
	file. If you can get into Mail successfully, then the corruption is in the MMF
	file.
	
	If the MMF is corrupt, you can not usually export messages. As a result, you
	should use the CheckMMF utility. To start the CheckMMF utility, hold the SHIFT
	and ENTER keys while you are logging into Mail.
	
	You can also restore the MMF from backup. You can use the Listuser utility to
	identify the correct HEX-ID.MMF. You can also use a personal backup of the MMF
	file.
	
	If a backup is not available or for additional information, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q126925 PC Win: How to Create a New MMF (Stored Locally)
	
	MORE INFORMATION
	================
	
	Corrupt MMFs are more likely to happen on the file server rather than the local
	drive because of the increased number of variables that can cause file
	corruption.
	
	The following are several reasons why MMFs can have corruption:
	
	Hardware reasons:
	
	- Faulty network interface cards
	
	- Pinched or frayed network cables
	
	- Bad sectors on hard drive platters
	
	- Server going down while writing file to disk
	
	- Bad RAM chips because files are cached in RAM
	
	- Bad system boards in servers
	
	Software Reasons:
	
	- Running out of disk space on the server (causing both a GP-Fault and
	  potentially corrupt the MMF
	
	- Abnormal termination of the spooler (reboot, loss of power, etc.)
	
	- Network drivers
	
	- Upper Memory Block providers
	
	- TSRs
	
	- Viruses
	
	- Memory corruption as a result of GPF of third party software
	
	Additional query words: 3.00b 3.20 3.20a GPF WFW 3.11
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMail320 kbMail300b kbMail320a
	Version           : WINDOWS:3.0b,3.2,3.2a
	
	=============================================================================
	

{% endraw %}
