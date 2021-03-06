---
layout: page
title: "Q148132: Swapable Floppy/CD-ROM Components Support on NEC Versa 4050C"
permalink: /kb/148/Q148132/
---

## Q148132: Swapable Floppy/CD-ROM Components Support on NEC Versa 4050C

{% raw %}

	Article: Q148132
	Product(s): Microsoft Windows NT
	Version(s): 3.50 3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The NEC Versa 4050C computer allows you to inter-exchange or swap between a
	floppy disk drive and an IDE CD-ROM drive. Windows NT does not allow you to
	start with any media component. For example, you cannot start Windows NT with a
	floppy disk drive and then immediately restart your component with a an IDE
	CD-ROM drive. A "STOP: 0x0000007B: Inaccessible Boot Device" blue screen appears
	if you start with a component that has not been configured in Windows NT.
	
	
	MORE INFORMATION
	================
	
	To start Windows NT on the NEC Versa 4050C computer:
	
	1. Configure the following devices to the recommended settings in Control Panel
	  Devices. If you start Windows NT with a floppy disk drive as one of your
	  hardware components, see Startup for Floppy in the table below. If you start
	  Windows NT with a CD-ROM drive as one of your hardware components, see
	  Startup for IDE CD-ROM.
	
	Device   Startup for Floppy   Startup for IDE CD-ROM
	------   ------------------   ----------------------
	ATDISK        BOOT                   SYSTEM
	ATAPI         BOOT                   BOOT
	FLOPPY        SYSTEM                 SYSTEM
	
	2. Verify that both ATAPI.SYS and ATDISK.SYS reside in the following directory:
	
	  %SystemRoot%\System32\Drivers
	
	  NOTE: Copy the missing file(s) from the Windows NT compact disc to the
	  directory mentioned above.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  ARTICLE-ID: Q125933
	  TITLE : STOP 0x0000007B: Inaccessible Boot Device After Removing CD-ROM
	
	The NEC products included here are manufactured by NEC Technologies, Inc., a
	vendor independent of Microsoft; we make no warranty, implied or otherwise,
	regarding these products' performance or reliability.
	
	Additional query words: 3.50 3.51 boot
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : 3.50 3.51
	
	=============================================================================
	

{% endraw %}
