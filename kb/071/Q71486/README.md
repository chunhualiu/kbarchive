---
layout: page
title: "Q71486: Structure of Interrupt Vector Table"
permalink: /kb/071/Q71486/
---

## Q71486: Structure of Interrupt Vector Table

{% raw %}

	Article: Q71486
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:1.x,2.x,3.x,4.x,5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 1.x, 2.11, 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 4.01, 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The bottom 1K (1024 bytes) of system memory is devoted to the storage of
	interrupt vectors. An interrupt vector is a 4-byte value of the form
	offset:segment, which represents the address of a routine to be called when the
	CPU receives an interrupt. Some vectors do not point to executable code, but
	rather to a data structure of some sort. For example, the vector for interrupt
	1Eh points to an 11-byte disk base table containing information on floppy
	drives. The interrupt vector table is a feature of the Intel 80x86/8088 family
	of microprocessors.
	
	MORE INFORMATION
	================
	
	Because each interrupt is a 4-byte value, the maximum number of vectors that can
	be stored in the interrupt vector table is 256. Each vector is located at
	segment:offset address: 0000:(int #)*4. Thus, the vector for int 24h (critical
	error) is located at address 0000:0090.
	
	For example, a partial hex dump of the interrupt vector table shows:
	
	  0000:0090    22 03 A1 2A .. .. .. .. .. .. .. .. .. .. .. ..
	
	The location that will be jumped to on int 24h is 2AA1:0322.
	
	Programming Considerations
	--------------------------
	
	While you can establish your own interrupt handlers by replacing the appropriate
	vector with the address of your handler routine, this approach is not advisable.
	A program can be interrupted before changing all four bytes of a vector, thus
	causing erroneous, possibly catastrophic, operation should the interrupt be
	issued. For this reason, and to ensure compatibility with future releases of
	MS-DOS, interrupt vectors should accessed using int 21h functions 25h (set
	interrupt vector) and 35h (get interrupt vector).
	
	REFERENCES
	==========
	
	"DOS Programmer's Reference" by Terry Dettmann, QUE Corporation
	
	"Advanced MS-DOS Programming" by Ray Duncan, Microsoft Press
	
	"The New Peter Norton Guide to the PC and PS/2," Microsoft Press
	
	Additional query words: 6.22 1.0 1.00 1.25 2.0 2.00 2.01 2.11 3.0 3.00 3.1 3.10 3.2 3.20 3.3 3.30 3.3a 3.30a 4.0 4.00 4.01 4.01a 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS1xSearch kbMSDOS320 kbMSDOS330a kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS401 kbMSDOS500a kbMSDOS211
	Version           : MS-DOS:1.x,2.x,3.x,4.x,5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
