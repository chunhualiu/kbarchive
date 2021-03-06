---
layout: page
title: "Q128921: Err Msg: The Device Has Been Disabled in Hardware... (Code 29)"
permalink: /kb/128/Q128921/
---

## Q128921: Err Msg: The Device Has Been Disabled in Hardware... (Code 29)

{% raw %}

	Article: Q128921
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Device Manager displays an exclamation point in a yellow circle for a PCI
	device. The status for this device reads:
	
	  The device has been disabled in the hardware. In order to use this
	  device, you must re-enable the hardware. See your hardware
	  documentation for details. (Code 29.)
	
	CAUSE
	=====
	
	This problem can occur for either of two reasons:
	
	- Windows 95 knows the hardware will not function.
	
	- The hardware is configured incorrectly.
	
	Windows 95 Knows the Hardware Will Not Function
	-----------------------------------------------
	
	Read the README.TXT file in the Windows folder to see if there is a known problem
	with the device. If the information in the README.TXT file does not help you
	solve the problem, please contact the device's manufacturer for additional
	instructions.
	
	The Hardware Is Configured Incorrectly
	--------------------------------------
	
	The problem may be due to a configuration error in your computer's BIOS. This can
	happen if the hardware is set to use resources that Windows 95 knows are not
	usable by the device. To verify that this is the problem, check the I/O range
	for the device. If the I/O range starts at 0, Windows 95 cannot activate the
	hardware.
	
	RESOLUTION
	==========
	
	You may be able to resolve the problem by removing the device and refreshing it
	on the PCI bus. This causes the PCI bus to be enumerated again and lets Windows
	95 reconfigure the hardware. To remove and refresh a PCI device, follow these
	steps:
	
	1. Click the Start button, point to Settings, then click Control Panel.
	
	2. Double-click the System icon.
	
	3. Click the Device Manager tab, click the PCI device, then click the Remove
	  button.
	
	  NOTE: The software for this device is removed from the current configuration
	  for your computer.
	
	4. Click the View Devices By Connection option button and then click PCI Bus.
	
	5. Click the Refresh button.
	
	  NOTE: The PCI device is detected, configured, and placed back in the Device
	  Manager.
	
	MORE INFORMATION
	================
	
	If you are not sure whether a device is a PCI device, follow these steps:
	
	1. Click the Start button, point to Settings, then click Control Panel.
	
	2. Double-click the System icon.
	
	3. Click the Device Manager tab, then click the View Devices By Connection
	  option button.
	
	4. Determine whether the device is on the PCI bus. If the device is on the PCI
	  bus, it is a PCI device. If the device is on the ISA or the EISA bus, the
	  device is not a PCI device.
	
	======================================================================
	Keywords          :  
	Technology        : kbWin95search kbZNotKeyword3
	
	=============================================================================
	

{% endraw %}
