---
layout: page
title: "Q126235: Flight Simulator: Fatal Error on DX/4 and OverDrive Processors"
permalink: /kb/126/Q126235/
---

## Q126235: Flight Simulator: Fatal Error on DX/4 and OverDrive Processors

{% raw %}

	Article: Q126235
	Product(s): Microsoft Home Games
	Version(s): MS-DOS:5.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbfile kbhw kbHardware
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Flight Simulator for MS-DOS, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to run the Setup program from Flight Simulator, version 5.0 on
	a computer using a 486 DX/4 processor or an Intel overdrive 63MHz Pentium
	processor (part number PODP5V63), you may receive the following error message:
	
	  FATAL error has occurred! Filename: FORN-000.FRN ERROR CODE: 8027
	
	This issue does not occur in Flight Simulator, version 5.1.
	
	RESOLUTION
	==========
	
	To resolve this issue, download and install the self-extracting Overdrv.exe
	file.
	
	NOTE: Do not install the Overdrv.exe file unless you experience this issue. The
	Overdrv.exe file is designed to run only on versions 5.0 and 5.0a of Microsoft
	Flight Simulator. This file contains beta drivers designed for use only on
	computers based on Intel Pentium or DX/4 overdrive processors. These drivers may
	not function correctly on all Intel Pentium- or DX/4 Overdrive-based computers.
	If you install the Overdrv.exe file on a computer based on a different processor
	or a computer running Microsoft Flight Simulator 5.1, Flight Simulator may not
	function properly.
	
	Obtaining the Overdrv.exe File
	------------------------------
	
	The following file is available for download from the Microsoft Download Center:
	
	  Overdrv.exe
	  (http://download.microsoft.com/download/fsim51dos/Patch/1/DOS/EN-US/Overdrv.exe)
	
	Release Date: May-24-1996
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. After it is posted, the file is housed on
	secure servers that prevent any unauthorized changes to the file.
	
	MORE INFORMATION
	================
	
	The Intel Overdrive processor is designed to replace the existing processor in
	an I486SX- or I486DX-based computer. The Overdrive processor is a retail product
	that is functionally identical to the Intel I486DX2 processor. The Intel I486DX2
	processor is sold only to original equipment manufacturers.
	
	For additional information about this issue, please see the following article in
	the Microsoft Knowledge Base:
	
	  Q108651 Flight Simulator: "Disk Error" or "Fatal Error Has Occurred"
	
	Additional query words: 5.00 flightsim fltsim dos d_fltsim microprocessor dx4/100 dx4\100 8027 dx4 over-drive
	
	======================================================================
	Keywords          : kbenv kberrmsg kbfile kbhw kbHardware 
	Technology        : kbGamesSearch kbFlightSimSearch kbFlightSim500DOS kbSimSearch
	Version           : MS-DOS:5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
