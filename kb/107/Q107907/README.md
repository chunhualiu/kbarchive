---
layout: page
title: "Q107907: Enhancements to Video for Windows, Version 1.1"
permalink: /kb/107/Q107907/
---

## Q107907: Enhancements to Video for Windows, Version 1.1

{% raw %}

	Article: Q107907
	Product(s): Microsoft PowerPoint for Windows
	Version(s): 1.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 26-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Video for Windows, version 1.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Video for Windows version 1.1 includes many enhancements and improvements. The
	following is a list and description of most of these changes.
	
	NEW COMPRESSORS AND DECOMPRESSORS
	---------------------------------
	
	The incorporation of Intel's Indeo version 3.1 and Supermac's Cinepak
	compression/decompression (codec) algorithms allows for higher screen
	resolutions (up to 320 x 240) or faster frame rates (up to 30 fps). Performance
	optimization for Windows files. Microsoft has significantly increased the
	performance of video images displayed under Windows with more efficient reading
	and rendering to the screen. This combination provides a 50-percent speed
	increase over 1.0.
	
	MORE FLEXIBLE ARCHITECTURE
	--------------------------
	
	Video for Windows applications can now include multiple data streams audio,
	video, still images, and text in a single file.
	
	INSTALLABLE RENDERERS
	---------------------
	
	These give developers tremendous creative freedom in determining how video images
	will be displayed to the screen. They can spin, flip, shrink, and dissolve video
	windows, and create other special effects.
	
	FILE HANDLERS
	-------------
	
	This improvements provides a common interface for accessing data from a
	time-based file (for example, animations, motion JPEG files, and proprietary
	formats) using Video for Windows.
	
	NEW APIs
	--------
	
	There are two new Windows classes that allow developers to do more with their
	video development: MCIWIND provides a common video playback interface for
	incorporating video playback into applications, and AVICAP provides a standard
	way to incorporate capture capability into applications.
	
	AUDIO COMPRESSION MANAGER/SOUND MAPPER FACILITY
	-----------------------------------------------
	
	Developers can now compress audio tracks using the Video for Windows built-in
	MSADPCM and IMA ADPCM audio codecs or codecs of their own. The sound mapper
	facility allows developers to author high-quality 16-bit audio files and play
	them back on 8 or 16-bit sound boards.
	
	INSTALLABLE COMPRESSION MANAGER
	-------------------------------
	
	This allows developers to install third-party codecs into Video for Windows.
	
	VIDEO CAPTURE DRIVER INTERFACE
	------------------------------
	
	Microsoft has defined a universal video capture driver interface that allows
	video capture board manufacturers to plug their products into the Video for
	Windows architecture.
	
	SUPPORT FOR 32-BIT DIBS
	-----------------------
	
	Video for Windows codecs can decompress to a higher resolution 32-bit DIB
	(device-independent bit map).
	
	MCI VCR SUPPORT
	---------------
	
	Third-party developers can write MCI VCR drivers using the VCR command set.
	
	NEW TOOLS
	---------
	
	Microsoft has added the following to the Video for Windows existing toolset of
	VIDCAP (for performing video capture), VIDEDIT (video editing) and Media Player
	(playback video), Microsoft has added the following:
	
	Screen Capture Utility:
	
	This allows developers to take any screen image or movement, place it in a Video
	for Windows file, and play it back. For example, a developer might create a
	video-based product demonstration by simply executing key product features on
	screen and capturing them for later playback by prospective customers.
	
	Visual Basic Custom Controls:
	
	Video for Windows provides Visual Basic 3.0 custom controls that allow developers
	to capture, edit or play Video for Windows files within any Visual Basic
	application.
	
	New Digital Video Clip Library:
	
	Microsoft has updated the video clip library that comes with Video for Windows by
	adding technical and general business sections.
	
	VISCA Controller:
	
	The VISCA protocol was developed by Sony as a way to interact with its consumer
	and professional video equipment (that is, camcorders, VCRs and so on). This MCI
	controller allows developers to step frame capture video sequences from video
	equipment, resulting in higher quality digital video.
	
	Updated Media Player:
	
	Media Player can now play back in OLE clients.
	
	VidTest Utility:
	
	The VidTest utility allows allows developers to test a PC's ability to play back
	digital video files.
	
	Cross-Platform Support:
	
	Video for Windows version 1.1 allows playback of Video for Windows files on the
	Macintosh, as well as the ability to take QuickTime files and convert them to a
	compressed AVI format.
	
	Additional query words: 1.1
	
	======================================================================
	Keywords          :  
	Technology        : kbVideoSearch kbVideo110
	Version           : :1.1
	
	=============================================================================
	

{% endraw %}
