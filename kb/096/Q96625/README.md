---
layout: page
title: "Q96625: MS-DOS: EMM386.EXE and VCPI Services"
permalink: /kb/096/Q96625/
---

## Q96625: MS-DOS: EMM386.EXE and VCPI Services

{% raw %}

	Article: Q96625
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0; WINDOWS:3.11
	Operating System(s): 
	Keyword(s): 
	Last Modified: 19-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system version 6.0 
	- Microsoft Windows for Workgroups version 3.11 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The information in this article applies to all versions of EMM386.EXE shown
	below:
	
	Product                                Version of EMM386.EXE
	----------------------------------------------------------
	MS-DOS 6.0                                    4.45
	MS-DOS 6.2 and 6.21                           4.48
	MS-DOS 6.22                                   4.49
	Windows for Workgroups 3.11                   4.48
	
	EMM386.EXE included with MS-DOS 6.x and Microsoft Windows for Workgroups version
	3.11 provides support for the Virtual Control Program Interface (VCPI) without
	having to set an expanded memory page frame and without having to specify a VCPI
	memory pool.
	
	VCPI services are provided by default--no special switches or parameters are
	required. If you want to disable VCPI support, you must use the NOVCPI switch on
	the EMM386.EXE command line in the CONFIG.SYS file.
	
	MORE INFORMATION
	================
	
	Several popular MS-DOS-based applications use DOS extenders to share extended
	memory and use of the protected mode of 80386 and higher processors through
	VCPI. VCPI is an extension to the expanded memory services (EMS) interface and
	is typically implemented by an EMS emulator (such as EMM386.EXE or Quarterdeck's
	QEMM386.SYS).
	
	Without VCPI support, "DOS-extended" applications could not run with systems
	running in virtual 8086 mode. EMS emulators use virtual 8086 mode to provide
	expanded memory mapping and/or create upper memory blocks (UMBs).
	
	To enable VCPI support in the version of EMM386.EXE provided with both MS-DOS 5.0
	and Windows 3.1, you must configure EMM386.EXE to emulate EMS. To enable VCPI
	without EMS support when the NOEMS switch is active, you must specify a VCPI
	memory pool size. For example, if you are using the version of EMM386.EXE from
	MS-DOS 5.0 or Windows 3.1, you can use the following command to provide 1
	megabyte of VCPI memory:
	
	  DEVICE=EMM386.EXE 1024 NOEMS
	
	The MS-DOS 6.x and Windows for Workgroups version of EMM386.EXE enables VCPI
	support without specifying a VCPI size parameter even if the NOEMS switch is
	active. Any EMM386 device command that does not include the NOVCPI switch
	provides VCPI services.
	
	With EMM386.EXE, VCPI memory is sized using the same parameters as the EMS pool
	size (EMM386 [memory] and MIN= parameters).
	
	REFERENCES
	==========
	
	For more information on the EMM386.EXE device driver and the NOVCPI switch,
	refer to MS-DOS Help; type the following at the MS-DOS command prompt:
	
	  " help emm386.exe " (without the quotation marks)
	
	Additional query words: 6.00 manager system exteners extenors
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbWFWSearch kbWFW311 kbMSDOSSearch kbMSDOS600
	Version           : MS-DOS:6.0; WINDOWS:3.11
	
	=============================================================================
	

{% endraw %}
