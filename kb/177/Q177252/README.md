---
layout: page
title: "Q177252: Flight Simulator: No Instructor or Voices in Lesson or Adventure"
permalink: /kb/177/Q177252/
---

## Q177252: Flight Simulator: No Instructor or Voices in Lesson or Adventure

{% raw %}

	Article: Q177252
	Product(s): Microsoft Home Games
	Version(s): 
	Operating System(s): 
	Keyword(s): kbenv kbsound kbui fs98 kbimu msgame
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Flight Simulator 98 
	- Microsoft Flight Simulator 2000 
	- Microsoft Flight Simulator 2000 Professional Edition 
	- Microsoft Flight Simulator 2002 
	- Microsoft Flight Simulator 2002 Professional Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you start a lesson, adventure, or flight in Microsoft Flight Simulator 98,
	Microsoft Flight Simulator 2000, or Microsoft Flight Simulator 2002, the
	Instructor, Pilot, or Air Traffic Controller (ATC) voices may not be played, or
	the engine sounds may not be played.
	
	CAUSE
	=====
	
	This behavior can occur if either of the following conditions is true:
	
	- An audio codec installed on the computer is missing or damaged.
	
	- The Flight Simulator 98 or 2000 disk is not inserted in the CD-ROM drive.
	
	- The lessons/adventures sound is disabled within the program.
	
	- The ATC option is disabled.
	
	- The sound driver for your sound card is outdated.
	
	- Your sound card does not support the necessary hardware features that are
	  needed to play the game.
	
	- You are playing in Multiplayer Mode.
	
	RESOLUTION
	==========
	
	To resolve this issue, verify that the Flight Simulator 98 or Flight Simulator
	2000 CD-ROM is inserted in the CD-ROM drive.
	
	For additional information about problems you may experience in Flight Simulator
	98 or Flight Simulator 2000 if the CD-ROM is not inserted in the CD-ROM drive,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q178383 Scenery, Airport, Adventures, VOR, Sound Problems Without Correct CD
	
	NOTE: If you are running Flight Simulator 2002 under a full installation, the
	CD-ROM is not required.
	
	If the issue continues to occur, proceed to the next method.
	
	Enable Sound
	------------
	
	1. Within the cockpit, click Options, point to Settings and then click Sound.
	
	2. Select the Lesson/Adventures or Air Traffic Control option. If this is
	  selected, move the lever to the right to increase the sound level.
	
	3. Click the green check mark or OK.
	
	Enable ATC in Flight Simulator 2002
	-----------------------------------
	
	1. Start Flight Simulator 2002.
	
	2. Click Create A Flight.
	
	3. Select Start Flight with ATC window open.
	
	4. Click Fly Now.
	
	If the issue continues to occur, proceed to the next method.
	
	Installing/Reinstalling Windows Audio Compression
	-------------------------------------------------
	
	If the issue continues to occur, install, or remove and reinstall, the missing or
	damaged audio codec. Use the appropriate steps below for your version of
	Windows:
	
	Microsoft Windows 9x or Windows Millennium Edition (Me)
	
	To verify that the audio and video compression components of Windows are properly
	installed, remove and reinstall Audio Compression and Video Compression. To do
	so, use the following steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs.
	
	3. On the Windows Setup tab, click Multimedia, and then click Details.
	
	4. Clear the Audio Compression and Video Compression options.
	
	5. Click OK, and then click Apply.
	
	6. Follow the instructions on the screen. You may be prompted to insert your
	  Windows CD-ROM or floppy disks.
	
	7. Exit Control Panel.
	
	For additional information about how to use remove and then reinstall audio/video
	compression, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q142731 How to Install and Remove Codecs and MCI Devices in Windows
	
	Microsoft Windows 2000
	
	For additional information bout how to change audio codecs in Microsoft Windows
	2000, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q254354 Reinstalling Audio Codecs or Media Control Devices in Windows 2000
	
	Reduce Hardware Sound Acceleration in Dxdiag
	--------------------------------------------
	
	If you run Combat Flight Simulator or Flight Simulator 98 on a computer that is
	running Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows 2000,
	reduce the Hardware Sound Acceleration setting:
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "dxdiag" (without the quotation marks), and then click
	  OK.
	
	3. On the Sound tab, under DirectX Features, move the "Hardware Sound
	  Acceleration Level" slider all the way to the left (the "No acceleration"
	  setting).
	
	4. Click Exit.
	
	If you are playing in multiplayer mode, then you will not hear the Air Traffic
	Control tower. This is by design.
	
	MORE INFORMATION
	================
	
	For additional information about how to troubleshoot problems with compressed
	audio in Microsoft Windows 95 or Microsoft Windows 98, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q133365 Windows 95/98: Troubleshooting Problems with Compressed Audio
	
	Additional query words: msgame fs98 fs2000 fs2k flightsim fltsim sound people speak talk vocal
	
	======================================================================
	Keywords          : kbenv kbsound kbui fs98 kbimu msgame 
	Technology        : kbGamesSearch kbFlightSimSearch kbFlightSim2000 kbFlightSim98 kbFlightSim2002 kbFlightSim2002Pro kbSimSearch
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
