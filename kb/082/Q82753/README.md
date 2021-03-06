---
layout: page
title: "Q82753: Printers with Limited TrueType Font Support"
permalink: /kb/082/Q82753/
---

## Q82753: Printers with Limited TrueType Font Support

{% raw %}

	Article: Q82753
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 14-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 3.1 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	The Windows 3.1 PRINTERS.WRI online document incorrectly states that the
	following printer drivers have limited support for TrueType (TT) fonts:
	
	- Canon LBP II
	
	- Canon LBP III
	
	- IBM LaserPrinter 4019
	
	- Olivetti PG306
	
	For example, PRINTERS.WRI states the following:
	
	  5.9 Printing TrueType Fonts on Canon Series II and III Laser
	      Printers
	
	      The Canon series II and III laser printers do not support
	      incremental downloading of TrueType fonts. To print TrueType
	      fonts by using one of these printers, you must select the
	      Enable TrueType Fonts check box in the printer setup dialog box
	      for the printer.
	
	In fact, these printers do support TrueType fonts. The only limitation is that TT
	fonts cannot be downloaded as soft fonts. Instead, TT fonts must be printed as
	graphics.
	
	MORE INFORMATION
	================
	
	TrueType is normally printed as a block of graphics. When TrueType fonts can be
	downloaded as soft fonts to the printer, printing is generally faster. The
	Windows printer driver can simply send a select font command followed by the
	ASCII characters to print. When Print TrueType As Graphics is selected, the
	Windows print driver must send a select graphics mode command followed by a
	large amount of binary data for the graphics band. The end result of both
	methods produces identical output; the only difference is in speed.
	
	PostScript printers and laser printers that use the Hewlett-Packard (HP) LaserJet
	Series II (and all later HP LaserJets) soft font download commands can download
	TrueType fonts to the printer as soft fonts. LaserJets earlier than the Series
	either lack soft font downloading ability (classic HP LaserJet) or use an
	incompatible soft font header (HP LaserJet Plus, 500). HP LaserJet compatible
	printers that emulate the HP LaserJet Plus share this problem. Use the Download
	TrueType As Graphics option for these printers.
	
	To select Print TrueType As Graphics
	------------------------------------
	
	1. Open Control Panel and choose the Printers icon.
	
	2. Select the printer from the list box and choose the Setup button.
	
	3. The Canon LBP II and LBP III, IBM LaserPrinter 4019, and Olivetti PG306 all
	  have a check box in the lower-left corner (the message reads Print TrueType
	  As Graphics or Enable TrueType Fonts).
	
	4. Select the check box, then close the Printer Setup dialog box.
	
	These printers will now print TrueType fonts.
	
	The only printers in the Windows 3.1 package that do not support TrueType fonts
	are TTY printers (which have no graphic support) and plotters (which have vector
	graphics, but neither bitmap graphics nor TrueType font support).
	
	
	Additional query words: 3.10 documentation error 3.11 win31
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin310
	Version           : WINDOWS:3.1
	
	=============================================================================
	

{% endraw %}
