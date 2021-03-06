---
layout: page
title: "Q132995: Games (I-Q) Requiring or Performing Better in MS-DOS Mode"
permalink: /kb/132/Q132995/
---

## Q132995: Games (I-Q) Requiring or Performing Better in MS-DOS Mode

{% raw %}

	Article: Q132995
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): win95 appscomp kbAppCompatibility
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article lists games (I-Q) that must be run in MS-DOS mode. Additional
	information is provided when available.
	
	For information about running games in MS-DOS mode, please see the "Running an
	Application in MS-DOS Mode" section later in this article.
	
	MORE INFORMATION
	================
	
	Inca,
	
	Inca MM CD by Sierra Online
	---------------------------
	
	Executable: INCA.EXE
	
	Inca programs the Direct Memory Access (DMA) controller incorrectly. It must be
	run in MS-DOS mode.
	
	
	Indy Car Racing by Papyrus
	--------------------------
	
	Executable: INDYCAR.EXE
	
	Indy Car Racing makes incorrect assumptions about the system memory configuration
	when Windows 95 is running, causing it to believe the computer has a negative
	amount of memory. It must be run in MS-DOS mode.
	
	It may be necessary to delete the existing INDYCAR.PIF file before running this
	program so that Windows can configure it properly.
	
	
	Inferno: The Odyssey Continues by Digital Image Design
	------------------------------------------------------
	
	Executable: INFERNO.BAT
	
	Inferno is distributed by Ocean Distributing. Inferno moves an active data
	segment which results in a system hang if that data segment is needed while it
	is being moved. This problem may be alleviated if you run Inferno in MS- DOS
	mode.
	
	
	Ishar 3 by Ready Soft
	---------------------
	
	Executable: START.EXE
	
	Ishar has a problem in its timing code that causes it to stop responding (hang).
	There are also problems with the MS-DOS extender used by Ishar.
	
	NOTE: Before installing this game, restart your computer, press F8 when you see
	the "Starting Windows 95" message, then choose Safe Mode Command Prompt Only
	from the Startup menu.
	
	
	Isle of the Dead by Merit Software
	----------------------------------
	
	Isle of the Dead requires MS-DOS mode.
	
	Jutland by Software Sorcery
	---------------------------
	
	Executables: JUTLAND.EXE, JUTLANDV.EXE
	
	Jutland does not run in Windows 95 due to an uninitialized variable. It must be
	run in MS-DOS mode.
	
	
	Kingdoms of England II - Vikings: Fields of Conquest by Realism
	Entertainment
	-----------------------------------------------------------------------------
	
	Executable: VIKINGS.EXE
	
	The MS-DOS extender used by Kingdoms of England is incompatible with Windows 95.
	It must be run in MS-DOS mode.
	
	
	King's Quest III by Sierra Online
	---------------------------------
	
	Executable: KQ3.BAT
	
	King's Quest III must run in MS-DOS mode due to the way it implements copy-
	protection.
	
	Lawnmower Man by Sales Curve
	----------------------------
	
	Executable: LAWN.BAT
	
	Lawnmower Man requires MS-DOS mode.
	
	Lemmings by Psygnosis
	---------------------
	
	Executable: LEMMINGS.BAT
	
	Lemmings manipulates expanded (EMS) memory in a manner incompatible with Windows
	95. It must be run in MS-DOS mode.
	
	
	Lemmings II - Tribes by Psygnosis
	---------------------------------
	
	Executable: L2.BAT
	
	Lemmings II uses the timer in a manner not compatible with Windows 95. It can be
	run in Windows 95, but does not run smoothly. Running in MS-DOS mode allows the
	program to run smoothly.
	
	
	Lemmings Chronicles by Psygnosis
	--------------------------------
	
	Executable: L3.BAT
	
	Lemmings Chronicles manipulates expanded (EMS) memory in a manner incompatible
	with Windows 95. It must be run in MS-DOS mode.
	
	
	Links 386 CD by Access Software
	-------------------------------
	
	Executables: GOLFCD.BAT, LINKSCD.BAT
	
	Links 386 moves an active code segment, resulting in a problem if that code
	segment is needed while it is being moved. The problem may be resolved in MS-DOS
	mode.
	
	
	Lost in Time by Sierra Online
	-----------------------------
	
	Lost in Time requires MS-DOS mode.
	
	Machiavelli the Prince by Microprose
	------------------------------------
	
	Executable: PRINCE.EXE
	
	Machiavelli the Prince uses Virtual Direct Memory Access Services (VDS)
	incorrectly. Depending on your system configuration, it may play static instead
	of sound and music. It may also hang when exiting due to another problem in the
	program. If you encounter either of these problems, run Machiavelli the Prince
	in MS-DOS mode.
	
	
	Mammals
	-------
	
	Executable: GO.BAT
	
	Mammals detects the hard disk as a network drive if run under Windows 95. It must
	be run in MS-DOS mode.
	
	Mechwarrior 2 by Activision
	---------------------------
	
	Executable: MECH2.EXE
	
	Mechwarrior 2 plays the intro movie, but when you go into combat, a page fault
	error occurs. The problem is resolved when the program is run in the MS-DOS
	mode.
	
	Menzoberranzan by Strategic Simulations (SSI)
	---------------------------------------------
	
	Executable: MENZO.EXE
	
	Menzoberranzan encounters internal assertion failures when run under Windows 95.
	It must be run in MS-DOS mode.
	
	Metaltech: Earthsiege by Sierra Online
	--------------------------------------
	
	Executables: ES.BAT, ES.EXE
	
	The way Metaltech uses the sound card is incompatible with Windows 95. It must be
	run in MS-DOS mode.
	
	Mickey's 1-2-3 by Disney
	------------------------
	
	Executable: MICKEY.BAT
	
	Mickey's 1-2-3 has a timing-related problem in its sound code that causes it to
	hang. The problem may be resolved when Mickey's 1-2-3 is run in MS-DOS mode.
	
	
	Microcosm by Psygnosis
	----------------------
	
	Executable: MCOSM.EXE
	
	Microcosm uses a memory model that is not compatible with Windows 95. It must be
	run in MS-DOS mode.
	
	
	MIG-29 by Spectrum Holobyte
	---------------------------
	
	MIG-29 requires MS-DOS mode.
	
	
	Mixed-up Mother Goose by Sierra Online
	--------------------------------------
	
	Executables: MGCD.BAT, MG.BAT
	
	Mixed-up Mother Goose has a timing-related problem in its sound code that causes
	it to hang. The problem may be resolved when the program is run in MS-DOS mode.
	
	
	More Lemmings by Psygnosis
	--------------------------
	
	More Lemmings manipulates expanded (EMS) memory in a manner incompatible with
	Windows 95. It must be run in MS-DOS mode.
	
	
	Mortal Kombat II by Acclaim Entertainment
	-----------------------------------------
	
	Executable: MKII.EXE
	
	Mortal Kombat II makes incorrect assumptions about the system memory
	configuration when Windows 95 is running. It must be run in MS-DOS mode.
	
	
	NASCAR Racing by Papyrus
	------------------------
	
	Executable: NASCAR.EXE
	
	NASCAR Racing makes incorrect assumptions about the system memory configuration
	when Windows 95 is running, causing it to believe the computer has a negative
	amount of memory. It must be run in MS-DOS mode.
	
	It may be necessary to delete the existing NASCAR.PIF file before running this
	program, so that Windows can configure it properly.
	
	NOTE: The 1.2 patch of NASCAR.EXE runs in Windows 95, with some reservations:
	
	- If this is the first MS-DOS-based program that uses the sound card after the
	  system is restarted, it hangs the system.
	
	- If this is the second MS-DOS-based program that uses the sound card, it works
	  correctly.
	
	- With this patch, the program works properly at any time if the sound card is
	  disabled in Device Manager.
	
	
	NBA Live '95 by Electronic Arts
	-------------------------------
	
	Executable: NBA.BAT
	
	NBA Live '95 has problems with timing and mixing sounds. It runs better in MS-DOS
	mode.
	
	
	NCAA Basketball - Road to the Final Four 2
	------------------------------------------
	
	Executable: NCAA2.BAT
	
	NCAA Basketball fails when it attempts to access protected-mode operating system
	data structures. It must be run in MS-DOS mode.
	
	
	One Must Fall by Epic
	---------------------
	
	Executable: OMF.EXE
	
	One Must Fall occasionally accesses memory it did not allocate. Windows 95 memory
	protection terminates the program due to an invalid operation. Run One Must Fall
	in MS-DOS mode to avoid the problem.
	
	One Must Fall comes with a custom .PIF file called OMF.PIF that you must delete
	before running One Must Fall. This allows Windows 95 to create a new OMF.PIF
	file that is properly configured.
	
	
	Oregon Trail Deluxe by MECC
	---------------------------
	
	Executable: OREGON.EXE
	
	Oregon Trail attempts to take control of the sound card if run under Windows 95.
	It must be run in MS-DOS mode for sound to work properly.
	
	Pacific Strike, by Origin
	-------------------------
	
	Executable: PACIFIC.EXE
	
	Pacific Strike requires Virtual Control Program Interface (VCPI) services, which
	are not supported by Windows 95. It must be run in MS-DOS mode.
	
	PGA Tour Golf 486 by Electronic Arts
	------------------------------------
	
	Executable: GOLF.EXE
	
	PGA Tour Golf 486 has a problem in its timing code that causes it to pause for
	long periods of time under certain conditions. You may also encounter general
	protection faults with certain hardware. The problems may be resolved in MS-DOS
	mode.
	
	
	Pinball 2000 by Expert Software
	-------------------------------
	
	Pinball 2000 requires MS-DOS mode.
	
	Pinball Arcade by 21st Century
	------------------------------
	
	Executable: ARCADE.BAT
	
	Pinball Arcade attempts to calibrate the computer in a manner not compatible with
	Windows 95. Running it in MS-DOS mode allows the calibration to succeed.
	
	
	Pinball Fantasies by 21st Century
	---------------------------------
	
	Executable: PINBALL.EXE
	
	Pinball Fantasies attempts to calibrate the computer in a manner not compatible
	with Windows 95. Running it in MS-DOS mode allows the calibration to succeed.
	
	
	The Playroom by Broderbund
	--------------------------
	
	The Playroom requires MS-DOS mode.
	
	NOTE: Before installing this game, restart your computer, press F8 when you see
	the "Starting Windows 95" message, then choose Safe Mode Command Prompt Only
	from the Startup menu.
	
	PowerHits BattleTech by ActiVision
	----------------------------------
	
	PowerHits BattleTech must be run in MS-DOS mode.
	
	PowerHits Movies by ActiVision
	------------------------------
	
	PowerHits Movies must be run in MS-DOS mode.
	
	Privateer by Origin
	-------------------
	
	Executable: PRIV.EXE
	
	Privateer uses the Virtual Control Programming Interface (VCPI) which is
	supported by Windows 95 only in MS-DOS mode.
	
	
	Putt-Putt Joins the Parade by Humongous Entertainment
	-----------------------------------------------------
	
	Putt-Putt Joins the Parade requires MS-DOS mode.
	
	Quarantine by GameTek
	---------------------
	
	Executable: Q.BAT
	
	Quarantine programs the sound card to a rate faster than it can handle. It must
	be run in MS-DOS mode.
	
	Running an Application in MS-DOS Mode
	-------------------------------------
	
	Windows 95 usually runs programs that require MS-DOS mode in MS-DOS mode
	automatically. If it does not, delete the corresponding .PIF file and
	double-click the program icon again. Note that .PIF files usually have the same
	name as the program file, but with a .PIF extension instead of the .BAT, .COM,
	or .EXE extension. The corresponding .PIF file can be found in one of the
	following locations:
	
	- In the folder that contains the program file.
	
	- In the hidden PIF folder in the Windows 95 folder.
	
	- In a folder specified by your PATH statement.
	
	To make certain you find all copies of the .PIF file, use the Find Files Or
	Folders feature.
	
	If Windows 95 does not configure the program to run in MS-DOS mode automatically,
	follow these steps:
	
	1. Click the executable file with the right mouse button, then click Properties
	  on the menu that appears.
	
	2. On the Program tab, click the Advanced button.
	
	3. Click the MS-DOS Mode check box to select it.
	
	4. You can usually use the Use Current MS-DOS Configuration option. However,
	  some programs may require that you use the Specify A New Configuration
	  option. Consult the program's documentation for sample CONFIG.SYS and
	  AUTOEXEC.BAT files.
	
	5. Click OK.
	
	These steps cause the program to run in MS-DOS mode. You may need to optimize the
	settings if the program requires a mouse, expanded memory, a CD-ROM drive, or a
	sound card. Consult the program's documentation to determine if it has specific
	needs.
	
	NOTE: You may have to double-click the program icon in Windows Explorer or My
	Computer, or type the program name in the Run dialog box, for the program's
	settings to take effect. Typing the program name at an MS-DOS prompt does not
	always cause the program's settings to be used.
	
	Additional query words: single sdam
	
	======================================================================
	Keywords          : win95 appscomp kbAppCompatibility 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
