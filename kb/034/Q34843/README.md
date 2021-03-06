---
layout: page
title: "Q34843: INFO: The Four Classes of Device Banding"
permalink: /kb/034/Q34843/
---

## Q34843: INFO: The Four Classes of Device Banding

{% raw %}

	Article: Q34843
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kb16bitonly kbOSWin310 _IK kbOSWin300 kbSDKWin16
	Last Modified: 02-JUL-1999
	
	3.00 3.10
	WINDOWS
	kbprg
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In the Microsoft Windows environment, banding is a common technique to divide a
	page into a number of sections, called bands. When an application uses banding,
	it requires less memory to produce a page of printed output at the potential
	expense of some additional time. This article discusses the four types of
	banding devices that can be used in the Windows environment: nonbanding devices,
	simple banding devices, "Full Page Banding for Text" devices, and BANDINFO
	devices.
	
	MORE INFORMATION
	================
	
	Nonbanding Devices
	------------------
	
	These devices do not perform any banding. PostScript printers and plotters are
	the most common nonbanding devices. These nonraster devices accept primitive
	output directly from Windows without any need for intermediate rasterization. An
	application can identify a nonbanding device by performing the following three
	steps:
	
	1. Create a Device Context (DC) for the output device and obtain a handle to the
	  device context (hDC).
	
	2. Call the GetDeviceCaps function, specifying the hDC and RASTERCAPS for the
	  iCapability parameter.
	
	3. Check the RC_BANDING bit of the GetDeviceCaps function. If the RC_BANDING bit
	  of the GetDeviceCaps return value is clear, the device does not perform
	  banding.
	
	Simple Banding Devices
	----------------------
	
	These devices divide both text and graphics into a series of bands starting at
	the top of each page and running to the bottom. Under versions of Windows
	earlier than 3.1, these devices may provide a full-page band when available
	memory permits, but they usually do not. Under Windows 3.1, these devices
	generally provide a full-page band when memory permits. Dot-matrix printers are
	the most common simple banding devices. An application can identify a simple
	banding device by performing previous 1 and 2 steps. The RC_BANDING bit is set
	for simple banding devices.
	
	"Full Page Banding for Text" Devices
	------------------------------------
	
	The driver for a page printer (commonly referred to as a laser printer) typically
	uses one band covering the full page for text followed by additional smaller
	bands for graphics. This technique is an optimization for a printer that allows
	text to be placed at any position on the page but does not have the graphics
	capabilities of a PostScript printer. Typically, a driver does not provide any
	graphics bands unless it detects a graphics command in its text band. While this
	technique allows the driver to optimize printing of pages containing only text,
	an application that prints graphics must call a graphics primitive in the text
	band to work correctly with this driver type. Most new page-printer drivers are
	developed for the fourth driver category, discussed in the following.
	
	BANDINFO Devices
	----------------
	
	With a BANDINFO device driver, an application can optimize its printing and
	eliminate calling graphics primitives in a text band by requesting graphics
	bands only when required and identifying which band is the text band. This
	BANDINFO escape provides this capability. An application issues the BANDINFO
	escape to inform the driver that the application will print graphics and to
	determine which bands contain text and which bands contain graphics.
	
	An application can use the QUERYESCSUPPORT escape to identify a device that
	supports the BANDINFO escape. If the driver supports BANDINFO, the application
	can determine when to print text or graphics as appropriate. If the driver does
	not support the BANDINFO escape, the application should print text and graphics
	in each band.
	
	The Hewlett-Packard LaserJet driver is an example of a printer driver that
	implements the BANDINFO escape.
	
	Additional query words: 3.00 3.10
	
	======================================================================
	Keywords          : kb16bitonly kbOSWin310 _IK kbOSWin300 kbSDKWin16 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
