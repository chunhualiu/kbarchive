---
layout: page
title: "Q63777: EDIT.COM Cannot Find QBASIC.EXE"
permalink: /kb/063/Q63777/
---

## Q63777: EDIT.COM Cannot Find QBASIC.EXE

{% raw %}

	Article: Q63777
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
	
	When EDIT.COM is executed in MS-DOS versions 5.0 and later, it invokes
	QBASIC.EXE with the /EDITOR switch. If QBASIC.EXE is not in either the same
	directory as EDIT.COM or on the path, EDIT.COM is unable to find QBASIC.EXE and
	the following message is displayed:
	
	  Cannot find file QBASIC.EXE
	
	You can correct this problem by using one of the following methods:
	
	- Add the directory that contains QBASIC.EXE to the path.
	
	- Copy QBASIC.EXE to a directory already on the path.
	
	- Copy QBASIC.EXE to the same directory as EDIT.COM.
	
	While none of these solutions is extremely complicated, the second and third
	solutions are easier than the first.
	
	MORE INFORMATION
	================
	
	For more information on this subject, query on the following words:
	
	  "qbasic" (without the quotation marks) and "edit.com" (without the quotation
	  marks)
	
	Additional query words: 6.22 5.00 5.00a 6.00 6.20
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
