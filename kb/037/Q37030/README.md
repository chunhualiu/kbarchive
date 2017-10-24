---
layout: page
title: "Q37030: BASIC Memory Model: Determining Segment Sizes with LINK /MAP"
permalink: /kb/037/Q37030/
---

## Q37030: BASIC Memory Model: Determining Segment Sizes with LINK /MAP

{% raw %}

	Article: Q37030
	Product(s): See article
	Version(s): 4.00 4.00b 4.50
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | SR# G881013-4601 B_BasicCom | mspl13_basic
	Last Modified: 28-DEC-1989
	
	QuickBASIC uses a medium memory model plus dynamic and huge (larger
	than 64K) dynamic arrays supported in far heap. With this model, a
	program may contain multiple code segments (up to 64K per module) and
	one 64K shared data segment (known as DGROUP). The space that is not
	used by the code and DGROUP at run time is left for allocation of
	dynamic and huge dynamic arrays.
	
	The LINK .MAP file can be used to determine the size of the code
	segment(s) and the static portion of the DGROUP segment, as shown
	below. However, the FRE function is easier to use than the LINK .MAP
	file for getting information about data allocation.
	
	This information applies to Microsoft QuickBASIC Versions 4.00, 4.00b
	and 4.50 for MS-DOS, to Microsoft BASIC Compiler Versions 6.00 and
	6.00b for MS-DOS and MS OS/2, and to Microsoft BASIC PDS 7.00 for
	MS-DOS and MS OS/2.
	
	Note that allocating longer variable-length strings consumes more
	DGROUP space at run time than is indicated by the initial, static
	DGROUP allocation shown in the LINK .MAP file.
	
	Rather than using the LINK .MAP file, a better method to determine
	data usage is to invoke the FRE function within a program at run time.
	FRE("") returns the amount of dynamic space free for strings and
	dynamic arrays in DGROUP. FRE(-1) returns the amount of space free for
	dynamic arrays in far heap.
	
	To generate a link map, use the /MAP switch for the linker (LINK
	/MAP). The following link map is generated by linking a module called
	DOG.OBJ and is explained further below:
	
	       Start  Stop   Length Name                   Class
	       00000H 00050H 00051H DOG_CODE               BC_CODE
	(Code  00060H 00297H 00238H _TEXT                  CODE
	 here) 00298H 008C5H 0062EH LOADRTM                CODE
	----------------------------------------------------------------
	(Data  008D0H 0167FH 00DB0H BR_DATA                BLANK
	 here) 01680H 01680H 00000H BR_SKYS                BLANK
	       01680H 01680H 00000H COMMON                 BLANK
	       01680H 01689H 0000AH BC_DATA                BC_DATA
	       0168AH 0168FH 00006H NMALLOC                BC_VARS
	       01690H 01690H 00000H ENMALLOC               BC_VARS
	       01690H 01690H 00000H BC_FT                  BC_SEGS
	       01690H 0169FH 00010H BC_CN                  BC_SEGS
	       016A0H 016A2H 00003H BC_DS                  BC_SEGS
	       016A4H 016A4H 00000H BC_SAB                 BC_SEGS
	       016A4H 016ABH 00008H BC_SA                  BC_SEGS
	       016ACH 016ACH 00000H _DATA                  DATA
	       016ACH 016C7H 0001CH CDATA                  DATA
	       016C8H 016C8H 00000H XCB                    DATA
	       016C8H 016CBH 00004H XC                     DATA
	       016CCH 016CCH 00000H XCE                    DATA
	       016CCH 016CCH 00000H XIFB                   DATA
	       016CCH 016CCH 00000H XIF                    DATA
	       016CCH 016CCH 00000H XIFE                   DATA
	       016CCH 016CCH 00000H XIB                    DATA
	       016CCH 016CCH 00000H XI                     DATA
	       016CCH 016CCH 00000H XIE                    DATA
	       016CCH 016CCH 00000H XPB                    DATA
	       016CCH 016CCH 00000H XP                     DATA
	       016CCH 016CCH 00000H XPE                    DATA
	       016CCH 016CCH 00000H XCFB                   DATA
	       016CCH 016CCH 00000H XCF                    DATA
	       016CCH 016CCH 00000H XCFE                   DATA
	       016CCH 016CCH 00000H XOB                    BSS
	       016CCH 016CCH 00000H XO                     BSS
	       016CCH 016CCH 00000H XOE                    BSS
	       016D0H 01ECFH 00800H STACK                  STACK
	
	 Origin   Group
	 008D:0   DGROUP
	
	In the above example, a source module called DOG.BAS was compiled and
	linked, resulting in a code segment name of DOG_CODE, which is limited
	to a maximum of 64K in size (if other compiler limitations are not
	exceeded first). DOG_CODE has the class name of BC_CODE. If your code
	module is approaching 64K in size, you should break it into SUBprogram
	and/or FUNCTION procedures in separate modules that can be compiled
	separately and then linked with the main module.
	
	The first three lines in the above map are the code segments. Each
	segment named can be up to 64K in size. Their classes are usually
	BC_CODE, CODE, and ENDCODE.
	
	The Origin section at the bottom of the link map tells you the
	position where the default data segment (DGROUP) starts, relative to
	the start of the .EXE code. The sum of the length of the items in
	DGROUP cannot exceed 64K. Items in DGROUP start at 008D:0 in the above
	map [which means offset 0 from the (16-byte) paragraph address 008D
	hex].
	
	For other programs, you may find another group, FMGROUP, whose origin
	is listed at the bottom of the link map (not shown in the above
	example). This group is used when you compile with the /AH option.
	FMGROUP is used for allocation tables and messages relating to far
	data. Arrays in far heap are not allocated space until run time.
	
	Note that the addresses given in the link map are not absolute load
	addresses -- instead, they are relative to the start of the code in
	the relocatable .EXE file. Only at run time does MS-DOS decide the
	absolute address where the .EXE program is loaded in memory. The
	VARPTR and VARSEG statements can then be used within a BASIC program
	to determine absolute addresses of variables and arrays at run time.
	Debuggers such as Microsoft CodeView, provided with the BASIC compiler
	Versions 6.00 and 6.00b, may also be used to determine absolute load
	locations at run time.

{% endraw %}