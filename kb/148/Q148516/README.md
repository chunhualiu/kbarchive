---
layout: page
title: "Q148516: WINNTP.EXE Fails If Windows 95 Boot Sector Is Installed"
permalink: /kb/148/Q148516/
---

## Q148516: WINNTP.EXE Fails If Windows 95 Boot Sector Is Installed

{% raw %}

	Article: Q148516
	Product(s): Microsoft Windows NT
	Version(s): 3.5,3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	- MSPRESS Microsoft Windows NT Resource Kit, versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you use WINNTP.EXE, a CPS utility in the Windows NT Resource Kit versions
	3.5 and 3.51, on a system that has Windows 95, it fails and the following error
	message appears:
	
	  Setup does not recognize the boot sector of drive X as that of a bootable
	  drive.
	
	  Setup cannot continue.
	
	where X is the drive letter of the active boot partition.
	
	CAUSE
	=====
	
	When you install Windows 95, the boot sector of the active partition is
	modified. WINNTP.EXE is not able to interpret the Windows 95 boot sector.
	
	WORKAROUND
	==========
	
	To work around this problem, do the following:
	
	1. Re-install Windows 95.
	
	2. Create a Windows 95 Boot disk and copy the Windows 95 SYS.COM to the disk.
	
	3. Boot the system to MS-DOS 6.22.
	
	4. Run WINNTP.EXE. Make sure you have the current version of the Emergency
	  Repair Disk.
	
	5. Use the Windows 95 Boot disk to boot the system.
	
	6. Use the Windows 95 SYS.COM to transfer the Windows 95 system files.
	
	7. Boot your system using the three Windows NT Boot floppy disks.
	
	8. Press R for Repair at the Windows NT "Welcome to Setup" screen.
	
	9. Clear the X from all Repair options except for Inspect Boot Sector and select
	  Continue.
	
	10. Press Enter at the Floppy/Hard Drive Detection screen.
	
	11. In the Mass Storage Detection screen, make sure that the correct adapter
	  driver has been detected. If it is correct, press Enter. If it is not
	  correct, press S to specify the correct adapter driver.
	
	12. Insert the Emergency Repair Disk when you are instructed to do so. The boot
	  sector is replaced and you must restart the computer.
	
	The system can now dual boot between Windows NT and Windows 95.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT Resource Kit versions
	3.5 and 3.51. We are researching this problem and will post new information here
	in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	WINNTP checks the logical sector zero offset 3 of the active partition for the
	OEM name of "MS-DOS 5.0" or "NTFS" (without quotation marks). This is done to
	determine a valid boot sector. The OEM name for Windows 95 is MSWIN4.0.
	
	
	Additional query words: prodnt 3.50 3.51 win95
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbMSPressSearch kbWinNTS351search kbWinNTS350search kbZNotKeyword6 kbZNotKeyword2 kbZNotKeyword5
	Version           : :3.5,3.51
	
	=============================================================================
	

{% endraw %}
