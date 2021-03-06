---
layout: page
title: "Q74985: Determining Load Size of Device Drivers or TSRs"
permalink: /kb/074/Q74985/
---

## Q74985: Determining Load Size of Device Drivers or TSRs

{% raw %}

	Article: Q74985
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Three size factors determine the space needed to load a device driver or TSR
	(terminate-and-stay-resident) program into the upper memory area (UMA). The most
	important of these factors is the size that must be available in one contiguous
	upper memory block (UMB) for the device driver or TSR to load high. These
	factors are as follows:
	
	Load Size
	---------
	
	The size of the device/TSR when it's first loaded, before it begins execution.
	Frequently this is the size of the file on the disk, but may be larger.
	
	Initialization Size
	-------------------
	
	The size of the device/TSR and any initialization space it may need. Frequently
	the initialization size is equal to load size, but it may be the largest of the
	three sizes.
	
	Final Size
	----------
	
	The amount of memory needed after the completion of the initialization process.
	Frequently the smallest of the three sizes. This is the size indicated by the
	MEM command using the /P or /C switches.
	
	MORE INFORMATION
	================
	
	Because of the lack of standards for device driver and TSR initialization, it is
	virtually impossible to determine the memory needed in any other manner than
	trial and error. Load size can be determined; however, initialization and final
	sizes will vary from program to program.
	
	Quantity 1
	----------
	
	For .COM files and device drivers that follow standard conventions (.SYS), the
	load size will be the file size on disk rounded up to the nearest paragraph (16
	bytes). Note that some .SYS files will actually be .EXE files. To determine
	this, look at the first two bytes of the file. If these bytes are MZ in ASCII or
	4D and 5A in hex, it is an executable file.
	
	Executable files (.EXE) files contain the load size information in the program
	header (.EXE file header). The .EXE file load size does not necessarily relate
	to the file size on disk. At an offset of 10 and 12 bytes respectively reside
	the minimum and maximum number of pages (16 bytes) needed by the executable file
	in addition to the file size. EXEHDR.EXE included with many programming products
	(including Microsoft C Compiler) will allow you to look at the .EXE file header
	information. From this information you will be able to approximate the load size
	of an .EXE program.
	
	For example, by running EXEHDR.EXE included with Microsoft C version 6.0a on
	EMM386.EXE, the following information will be displayed:
	
	Microsoft (R) EXE File Header Utility  Version 2.01
	Copyright (C) Microsoft Corp 1985-1990.  All rights reserved.
	
	Library:                        LoadHi
	Description:                    Win386 LoadHi Device  (Version 1.0)
	Module type:                    Dynamic link library; initialization
	global
	                               NO external fixups in executable image
	Number of memory pages:         00000005 (5)
	Initial CS:EIP:                 object 3 offset 00000000
	Initial SS:ESP:                 object 0 offset 00000000
	Automatic data object:          0
	
	no. virtual  virtual  page     file     flags
	     address   size    map      pages
	0001 00000000 00001a08 00000001 00000002 EXECUTABLE, READABLE,
	                               PRELOAD, 32-bit
	0002 00002000 00001218 00000003 00000002 EXECUTABLE, READABLE,
	                                        DISCARDABLE, 32-bit
	0003 00004000 0000002a 00000005 00000001 EXECUTABLE, READABLE,
	                                        16:16 ALIAS
	
	Exports:
	ord obj  offset    name
	 1   1  000012e4  LoadHi_DDB exported, shared data
	
	By totaling the virtual sizes of 1a08H, 1218H, and 02AH you can determine the
	load size to be a total of 11338 decimal. Note that this is not necessarily the
	ending memory used by EMM386.EXE, but the initial load size.
	
	Quantity 2
	----------
	
	Many device drivers undergo an initialization process that normally requires more
	memory than the ending size of the driver. Frequently the initialization memory
	is placed after the device driver and subsequently freed upon completion of the
	initialization process. The method for doing so is not standardized, and
	therefore not consistent. For this reason, there is no way of knowing what
	method a driver developer will use, and therefore no way of determining how much
	memory will be used, other than by actually disassembling the code and working
	through the program.
	
	Quantity 3
	----------
	
	The final quantity, the Break address of the driver, is returned during the INIT
	procedure of a device driver or the termination call of a TSR.
	
	When loading a device driver, DOS will pass the device driver a command code 0
	for initialization. It is the device driver's responsibility to fill the Request
	Header (a DOS data structure) with the break address (ending address) of the
	device driver. When and where the code is located that the device driver uses to
	accomplish this task is completely up to the programmer. For this reason, the
	only way of determining the break address is to debug the device driver.
	
	A TSR program will make a DOS function call to one of the following functions:
	
	     Int 21h function 00h
	     Int 21h function 31h
	     Int 21h function 4Ch
	     Int 27h
	
	The program will provide DOS with the break address of the TSR via different
	methods depending upon the function used.
	
	REFERENCES
	==========
	
	"Microsoft MS-DOS Encyclopedia," pages 450-60
	"The Programmer's PC Sourcebook" by Thom Hogan
	"Microsoft Systems Journal," vol. 6, no. 4, July 1991
	"MS-DOS Functions" by Ray Duncan
	
	Additional query words: 6.22 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
