---
layout: page
title: "Q83331: DR DOS Policy and Workaround: Fault in MS-DOS Extender Error"
permalink: /kb/083/Q83331/
---

## Q83331: DR DOS Policy and Workaround: Fault in MS-DOS Extender Error

{% raw %}

	Article: Q83331
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): win31
	Last Modified: 01-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses the use of Microsoft Windows version 3.1 with Digital
	Research DOS (DR DOS).
	
	Microsoft can only ensure the stability of Microsoft Windows running on MS-DOS or
	PC-DOS versions 3.1 or later. Digital Research has released a software update
	for running Windows with DR DOS. Microsoft neither endorses nor ensures the
	stability of Microsoft Windows 3.1 running on DR DOS with or without the Digital
	Research software update.
	
	Microsoft Windows version 3.1 may give the following message when it enters the
	graphical user interface (GUI) mode of Windows Setup:
	
	  Standard Mode: Fault in MS-DOS Extender
	
	The error is caused by one of the following:
	
	- Attempting to set up Windows 3.1 on an operating system not formally tested
	  by Microsoft, such as DR DOS.
	
	- The virtual control program interface (VCPI) server being used does not
	  implement VCPI completely or correctly. (An example of a VCPI server is
	  EMM386.EXE.)
	
	Microsoft Windows 3.1 enters protected mode operation using DOSX.EXE during
	Setup. An operating system or VCPI server that is incompatible will cause
	DOSX.EXE to load improperly, thus causing Setup to fail and report:
	
	  Standard Mode: Fault in MS-DOS Extender
	
	MORE INFORMATION
	================
	
	If this occurs when you are attempting to upgrade from Windows 3.0 to Windows
	3.1, you will be unable to use Windows. The following set of instructions will
	allow you to return to a functional Windows 3.0 installation after a failed
	installation of Windows 3.1.
	
	NOTE: These steps do NOT work if you have successfully completed the installation
	of Windows 3.1 or you have attempted to install Windows 3.1 more than once.
	
	1. Restart the computer to clear the machine state.
	
	2. Rename all the .INI files and .GRP files in the Windows directory to .INN and
	  .GRN. For example, type the following at the MS-DOS command prompt:
	
	  rename *.ini *.inn
	  rename *.grp *.grn
	
	3. Delete the file WINVER.EXE from the Windows directory. This will allow
	  Windows 3.0 to update all of the Windows files.
	
	4. Reinstall Windows 3.0 to the Windows directory with the configuration options
	  used previously when you attempted to install Windows 3.1.
	
	5. Do not select any of the options in the graphics mode of Windows 3.0 Setup
	  (that is, Printers, Setup applications, Read documents, modify CONFIG.SYS,
	  AUTOEXEC.BAT).
	
	6. Copy all the .INN files and .GRN files to the same name with the original
	  extensions (.INI and .GRP.), by typing the following at the MS-DOS command
	  prompt:
	
	  copy *.inn *.ini
	  copy *.grn *.grp
	
	7. Copy SYSINI.W31 and WININI.W31 to SYSTEM.INI and WIN.INI, respectively, by
	  typing the following at the MS-DOS command prompt. The .W31 files are the
	  backup. INI files Windows 3.1 created during the attempted upgrade to Windows
	  3.1.
	
	  copy sysini.w31 system.ini
	  copy winini.w31 win.ini
	
	All OLE functionality will be intact for pre-Windows 3.1 OLE applications such as
	Microsoft Excel 3.0 and Microsoft Word for Windows 2.0.
	
	You should find a file named W8D40P2T.A4G in the Windows directory. This file is
	used by Windows 3.1 to start the graphics mode of setup. This file can be
	deleted.
	
	NOTE: The SETUP.INF file for Windows 3.0 may need to be temporarily adjusted to
	allow Windows 3.0 to set up on a system with limited hard drive space. Copy
	SETUP.EXE and SETUP.INF from Windows 3.0 Disk 1 to a separate directory on the
	hard disk. Use an MS-DOS based editor to edit the [DATA] section of the
	SETUP.INF for Windows 3.0, as follows:
	
	  [DATA]
	     neededspace386=6300000
	     space386upgrade=2000
	     neededspace286=4500000
	     space286upgrade=1000
	
	Set the values for both neededspace386 and neededspace286 to 1.
	
	Run Setup from the directory with the adjusted SETUP.INF. After Setup is
	complete, copy the Windows 3.0 SETUP.INF from Disk 1 to the Windows 3.0 SYSTEM
	directory.
	
	For additional information on making DR DOS compatible with Windows 3.1, or to
	obtain the DR DOS software update, please contact Digital Research.
	
	
	DR DOS is a registered trademark of Novell.
	
	
	REFERENCES
	==========
	
	Windows Resource Kit 2.0, page 15
	
	Additional query words: 3.10 3.1 DR DOS DRDOS dr-dos uninstall revert go back
	
	======================================================================
	Keywords          : win31 
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
