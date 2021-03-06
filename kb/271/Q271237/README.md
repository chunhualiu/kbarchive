---
layout: page
title: "Q271237: Magic School Bus: Sound Is Not Played in Program"
permalink: /kb/271/Q271237/
---

## Q271237: Magic School Bus: Sound Is Not Played in Program

{% raw %}

	Article: Q271237
	Product(s): Microsoft Home Kids Products
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbenv kbsound mskids kbimu
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Scholastic's Magic School Bus series: Explores Bugs, version 1.0 
	- Scholastic's Magic School Bus series: Explores the World of Animals for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Solar System for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Rainforest for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Ocean for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores the Human Body for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores in the Age of Dinosaurs for Windows, version 1.0 
	- Scholastic's Magic School Bus series: Explores Inside the Earth for Windows, version 1.0 
	- Scholastic's Magic School Bus Series: Volcanoes, version 1.0 
	- Scholastic's The Magic School Bus in Concert 
	- Scholastic's The Magic School Bus Lands on Mars 
	- Scholastic's The Magic School Bus Discovers Flight, version 1.0 
	- Scholastic's The Magic School Bus Whales and Dolphins, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use one of the programs listed at the beginning of this article, no
	sound may be played in the program.
	
	CAUSE
	=====
	
	This behavior can occur if the Microsoft Windows audio compression codecs are
	not properly installed on your computer, or if the priority levels of the audio
	compression codecs are not correctly set.
	
	RESOLUTION
	==========
	
	To resolve this issue, use following methods in the order in which they are
	presented.
	
	Uninstall and Reinstall the Audio Compression Codecs
	----------------------------------------------------
	
	To uninstall and reinstall the audio compression codecs:
	
	1. Quit all programs that are running on your computer.
	
	2. Click Start, point to Settings, and then click Control Panel.
	
	3. Double-click Add/Remove Programs.
	
	4. Click the Windows Setup tab.
	
	5. In the Components box, click to clear the Multimedia check box.
	
	6. Click Apply.
	
	7. In the Components box, click to select the Multimedia check box.
	
	8. Click Apply. If you are prompted to insert the Microsoft Windows CD-ROM, do
	  so.
	
	9. Close Control Panel, and then restart the computer.
	
	To remove and reinstall Audio Codecs in Windows 2000, you will need to follow the
	steps listed the articles below:
	
	  Q276423 How to Reinstall Audio and Video Codecs in Windows 2000
	
	  Q254354 Reinstalling Audio Codecs/Media Control Devices in Windows 2000
	
	If the issue continues to occur, proceed to the next method.
	
	Manually Set the Priority Levels
	--------------------------------
	
	You may need to manually set the priority levels for the Microsoft PCM Converter,
	the IMA ADPCM codec, and the Microsoft ADPCM codec.
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Multimedia.
	
	3. On the Audio tab, click to select the "Use only preferred devices" check box.
	
	4. Click the Devices or the Advanced tab.
	
	5. Click the plus sign (+) next to Audio Compression Codecs to expand the
	  branch.
	
	6. Double-click Microsoft PCM Converter.
	
	7. Click "Use this audio codec".
	
	8. In the "Change priority from <number> to" box, click 1.
	
	9. Click OK.
	
	10. Double-click Microsoft IMA ADPCM CODEC.
	
	11. Click "Use this audio codec".
	
	12. In the "Change priority from <number> to" box, click 2.
	
	13. Click OK.
	
	14. Double-click Microsoft ADPCM CODEC.
	
	15. Click "Use this audio codec".
	
	16. In the "Change priority from <number> to" box, click 1.
	
	17. Click OK, and then click OK again.
	
	18. Close Control Panel, and then restart the computer.
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article.
	
	Additional query words: 1.00 mskids schoolbus msb msbmars msbconcert quiet silence silent
	
	======================================================================
	Keywords          : kbenv kbsound mskids kbimu 
	Technology        : kbHomeProdSearch _IKkbbogus kbZNotKeyword kbKidsSearch kbScholasticVolcanoes kbScholasticHuman kbScholasticOcean kbScholasticSolar kbScholasticBugs kbScholasticDinosaurs kbScholasticEarth kbScholasticRainForest kbScholasticAnimals kbScholasticFlight kbScholasticMars kbScholasticWhales kbMSBSearch
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
