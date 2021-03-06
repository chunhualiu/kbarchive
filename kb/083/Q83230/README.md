---
layout: page
title: "Q83230: Determining the Default EXETYPE Value in Microsoft LINK"
permalink: /kb/083/Q83230/
---

## Q83230: Determining the Default EXETYPE Value in Microsoft LINK

{% raw %}

	Article: Q83230
	Product(s): Microsoft Programming Utilities
	Version(s): 
	Operating System(s): 
	Keyword(s): kb16bitonly
	Last Modified: 08-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft LINK for MS-DOS 
	- Microsoft LINK for OS/2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Beginning with version 5.3, the Microsoft Segmented Executable Linker can create
	executable files for three different operating systems: MS-DOS, Microsoft
	Windows, and OS/2. LINK determines the executable file type (EXETYPE) unless it
	is specified explicitly in the module- definition (.DEF) file. The EXETYPE
	defaults to a different type depending on the host operating system, the
	presence of the .DEF file, and the presence of imported or exported symbols. The
	following chart summarizes the default EXETYPE values:
	
	--------------------------------------------------------------------
	|Host Operating | No .DEF File | .DEF File |Imports/Exports in Module|
	|   System      |   Present    |  Present  |and No .DEF File Present |
	--------------------------------------------------------------------
	|               |              |           |                         |
	|    MS-DOS     |     MS-DOS   |  Windows  |          MS-DOS         |
	|               |              |           |                         |
	--------------------------------------------------------------------
	|               |              |           |                         |
	|     OS/2      |     OS/2     |  Windows  |           OS/2          |
	|               |              |           |                         |
	--------------------------------------------------------------------
	
	In previous versions of the Segmented Executable linker, OS/2 is the default
	EXETYPE when a .DEF file is present.
	
	MORE INFORMATION
	================
	
	EXETYPE [<descriptor>] statement specifies the target operating system
	with which an application is designed to run. The <descriptor> value can
	be one of the following values:
	
	  Descriptor           Meaning
	  -------------------------------------------------------------------
	WINDOWS [<version>]  Microsoft Windows. Default EXETYPE value. The
	                       <version> parameter specifies the minimum
	                       version of Windows needed to load the
	                       application or dynamic-link library (DLL). The
	                       syntax for <version> is as follows:
	
	                          <number>[.[<number>]]
	
	                       where each <number> is a decimal integer.
	
	  DOS                  Nonsegmented executable file. LINK assumes
	                       EXETYPE DOS for an overlaid MS-DOS program.
	
	  OS/2                 OS/2 version 1.x segmented executable file.
	
	  UNKNOWN              Other applications.
	
	Additional query words: kbinf 5.30 5.31 5.31.009 5.50 LinkIss
	
	======================================================================
	Keywords          : kb16bitonly 
	Technology        : kbAudDeveloper kbZNotKeyword3 kbLINKSearch
	Version           : :
	
	=============================================================================
	

{% endraw %}
