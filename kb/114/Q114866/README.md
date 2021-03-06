---
layout: page
title: "Q114866: Bookshelf 1994: Manual Installation Instructions"
permalink: /kb/114/Q114866/
---

## Q114866: Bookshelf 1994: Manual Installation Instructions

{% raw %}

	Article: Q114866
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1994 edition
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Bookshelf for Windows 1994 edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides instructions to manually install Microsoft Bookshelf for
	Windows, 1994 edition.
	
	MORE INFORMATION
	================
	
	To manually install Bookshelf, use the instructions below. These instructions
	assume:
	
	- Your hard disk is drive C
	
	- Your destination folder (directory) is C:\Books94
	
	- Your Windows folder is C:\Windows
	
	- Your CD-ROM drive is drive D
	
	If your hard disk drive, destination folder, Windows folder, or CD-ROM drive
	letters are different, replace the drive letters and folder names throughout
	this article with the drive letters and folder names on your computer.
	
	Windows 95 or Windows NT
	------------------------
	
	NOTE: The following instructions discuss copying, editing, and modifying files
	and folders. For more information about accomplishing these tasks in Windows,
	see your Windows printed documentation or online Help.
	
	Follow these steps if you are using Microsoft Windows 95 or Microsoft Windows NT.
	When copying files, DO NOT overwrite ANY existing files.
	
	CAUTION: Allowing the system files to be overwritten in Windows 95 or Windows NT
	may cause improper system performance.
	
	1. Create a folder named Books94 on drive C. For example, type the following at
	  the MS-DOS command prompt and press ENTER:
	
	  "md c:\books94" (without the quotation marks)
	
	2. Copy the following files from the D:\Bs94 folder to the C:\Books94 folder:
	
	   - Bs94.exe
	
	   - Qkeyslib.dll
	
	   - Mvbrkr11.dll
	
	   - Qshelf.exe
	
	   - Mvfs11.dll
	
	   - Qshelf.hlp
	
	  For example, type the following at the MS-DOS command prompt on drive C, and
	  press ENTER:
	
	  "copy d:\bs94\bs94.exe c:\books94" (without the quotation marks)
	
	3. Copy the file Bshelf93.exe from the D:\Sys folder to the C:\Windows folder.
	  For example, from the MS-DOS command prompt on drive C, type the following
	  and press ENTER:
	
	  "copy d:\sys\bshelf93.exe c:\windows" (without the quotation marks)
	
	  NOTE: The file is named BSHELF93.EXE to allow for backward compatibility)
	
	4. Install the fonts with Control Panel using the following steps:
	
	  a. From the Control Panel window, double-click Fonts.
	
	  b. On the File menu, click Install New Font.
	
	  c. Change the drive to your CD-ROM drive.
	
	  d. Double-click the Sys folder
	
	  e. Click Select All to select all fonts.
	
	  f. Make sure the "Copy fonts to..." box is checked.
	
	  g. Click the OK button.
	
	5. Use a text editor, such as Microsoft Notepad, to make the following changes
	  to the BS94.ini file, which is located in the Windows folder. If the BS94.ini
	  file does not already exist, create one in the Windows folder with these
	  entries:
	
	        [options]
	        drive=D:
	        sounds=1
	        ToolTips=1
	
	        [find]
	        Near=50
	
	        [colors]
	        JumpColor=255 0 255
	        PopUpColor=0 255 0
	
	6. Use a text editor to make the following changes to the Windows information
	  files, which are located in the Windows folder:
	
	  Changes to the Win.ini File
	
	        [mci extensions]
	        wav=waveaudio
	        mid=sequencer
	        rmi=sequencer
	        avi=AVIVideo
	        mmm=MMMovie
	
	        [Bookshelf]
	        APP=C:\BOOKS94\BS94.EXE
	
	  Changes to the System.ini File
	
	        [mci]
	        AVIVideo=mciavi.drv
	
	        [drivers]
	        MSACM.msadpcm=msadpcm.acm
	        MSACM.msgsm610=msgsm610.acm
	        VIDC.MSVC=msvidc.drv
	        VIDC.CVID=iccvid.drv
	
	        [MSACM.msgsm610]
	        MaxRTDecodeSamplesPerSec=11025
	
	7. Add the shortcuts using the appropriate section below as a guide.
	
	8. Exit Windows and restart the computer. The installation is now complete.
	
	Creating Start Menu Shortcuts
	-----------------------------
	
	To add Bookshelf 1994 to the Start Menu, do the following:
	
	1. Click the Start button, point to Settings, and then click Taskbar.
	
	2. Click the Start Menu Programs tab.
	
	3. Click Add.
	
	4. Type the following in the Command Line box, and then click Next:
	
	  "c:\books94\bs94.exe" (without the quotation marks)
	
	5. In the Select Program Folder dialog box, click the Microsoft Multimedia
	  folder to select it, and then click Next.
	
	  If Microsoft Multimedia is not listed, do the following to create it:
	
	  a. On the File Menu, click New Folder
	
	  b. Type the following, and then click Next:
	
	  "Microsoft Multimedia" (without the quotation marks)
	
	6. In the Select A Title For The Program dialog box, type the following, and
	  then click Finish:
	
	  "Bookshelf 1994" (without the quotation marks)
	
	7. Repeat steps 3 through 6 to create the remaining shortcuts:
	
	  Command Line: c:\books94\qshelf.exe
	  Select A Title: Quickshelf 1994
	
	  Command Line: c:\windows\notepad.exe
	  c:\books94\readme.txt
	  Select A Title: Bookshelf 1994 Readme
	
	8. If you want Quickshelf to start whenever Windows starts, create a QuickShelf
	  shortcut in the Startup folder. Repeat steps 3 through 6 using the
	  information for Shortcut 2, but select the Startup folder instead of the
	  Microsoft Multimedia folder.
	
	Windows 3.x
	-----------
	
	NOTE: The following instructions discuss copying, editing, and modifying files
	and folders. For more information about accomplishing these tasks in Windows,
	see your Windows printed documentation or online Help.
	
	If you are running Microsoft Windows 3.x, follow these steps. When copying files,
	exit Windows and copy from the MS-DOS command prompt. Allow MS-DOS to overwrite
	any files it finds already on your hard drive.
	
	1. Follow steps 1-3 in the Windows 95 section above.
	
	2. Copy the following files from the D:\Sys folder to the C:\Windows\System. For
	  example, from the MS-DOS command prompt on drive C, type the following and
	  press ENTER:
	
	  "copy d:\sys\msadpcm.acm c:\windows\system" (without the quotation marks)
	
	  - MSADPCM.ACM
	  - MCIAVI.DRV
	  - MSGSM610.ACM
	  - MSACM.DRV
	  - MMP.DLL
	  - MSVIDC.DRV
	  - MSACM.DLL
	  - ICCVID.DRV
	  - MSVIDEO.DLL
	
	3. The Bookshelf program installs special TrueType fonts. To install the fonts
	  through Control Panel, do the following:
	
	  a. Double-click the Fonts icon.
	
	  b. Click Add.
	
	  c. In the Add Fonts dialog box, select drive D from the Drives list. From the
	     Directories list, select the SYS folder.
	
	  d. Click Select All to select the following:
	
	  - Arial (True Type)
	  - Arial Bold (True Type)
	  - Arial Bold Italics (True Type)
	  - Arial Italics (True Type)
	  - Bookshelf Symbol 1 (True Type)
	  - Bookshelf Symbol 2 (True Type)
	  - Bookshelf Symbol 3 (True Type)
	  - Symbol (True Type)
	
	  e. Make sure the Copy Fonts To option is selected, and click OK.
	
	  f. Click Close.
	
	4. Use a text editor, such as Microsoft Notepad, to make the following changes
	  to the BS94.ini file, which is located in the Windows folder. If the BS94.ini
	  file does not already exist, create one in the Windows folder with these
	  entries:
	
	        [options]
	        drive=D:
	        sounds=1
	        ToolTips=1
	
	        [find]
	        Near=50
	
	        [colors]
	        JumpColor=255 0 255
	        PopUpColor=0 255 0
	
	5. Use a text editor to make the following changes to the Windows information
	  files, which are located in the Windows folder:
	
	  Changes to the Win.ini File
	
	        [mci extensions]
	        wav=waveaudio
	        mid=sequencer
	        rmi=sequencer
	        avi=AVIVideo
	        mmm=MMMovie
	
	        [Bookshelf]
	        APP=C:\BOOKS94\BS94.EXE
	
	  Changes to the System.ini File
	
	        [mci]
	        AVIVideo=mciavi.drv
	
	        [drivers]
	        MSACM.msadpcm=msadpcm.acm
	        MSACM.msgsm610=msgsm610.acm
	        VIDC.MSVC=msvidc.drv
	        VIDC.CVID=iccvid.drv
	
	        [MSACM.msgsm610]
	        MaxRTDecodeSamplesPerSec=11025
	
	6. Add the Bookshelf icons to Program Manager by following the instructions at
	  the end of this article.
	
	7. Exit Windows and restart the computer. The installation is complete.
	
	Creating Program Manager Icons
	------------------------------
	
	If you use the Windows Program Manager, use the following instructions to create
	the Bookshelf 1994 icons:
	
	1. Open the Microsoft Multimedia group. If this group does not already exist,
	  create it as follows:
	
	  a. On the File menu, click New.
	
	  b. Click Program Group, and then click OK.
	
	  c. In the Description box, type the following, and then click OK:
	
	  "Microsoft Multimedia" (without the quotation marks)
	
	2. On the File menu, click New.
	
	3. Click Program Item, and then click OK.
	
	4. Type the Description and Command Line information as listed below, and then
	  click OK:
	
	  "Description: Bookshelf 1994
	  Command Line: c:\books94\bs94.exe" (without the quotation marks)
	
	5. Repeat steps 2 through 4 to create the remaining items:
	
	  Description: Quickshelf 1994
	  Command Line: c:\books94\qshelf.exe
	
	  Description: Bookshelf 1994 Readme
	  Command Line: c:\windows\notepad.exe
	  c:\books94\readme.txt
	  Working Directory: c:\books94
	
	6. If you want Quickshelf to start whenever Windows starts, create a QuickShelf
	  icon in the Startup group. Open the Startup group, and then repeat steps 2
	  through 4 using the information for Item 2.
	
	Manual Integration of Bookshelf with Word 2.0 or 6.0 for Windows
	----------------------------------------------------------------
	
	These instructions assume:
	
	- Your hard disk is drive C
	
	- Your destination folder (directory) is C:\Books94
	
	- Your Windows folder is C:\Windows
	
	- Your Word for Windows folder is C:\Winword
	
	- Your CD-ROM drive is drive D
	
	If your hard disk drive, destination folder, Windows folder, Winword folder or
	CD-ROM drive letters are different, replace the drive letters and folder names
	throughout this article with the drive letters and folder names on your
	computer.
	
	To manually integrate Bookshelf with Word for Windows 2.0 or 6.0, do the
	following:
	
	1. Copy D:\Word\Bshelf94.dot to the C:\Winword\Startup folder.
	
	2. Copy D:\Word\Bookshlf.dll to the C:\Windows\System folder.
	
	3. Copy D:\Word\Bsword.hlp to the C:\Books94 folder.
	
	4. After you copy these files to the hard drive, you need to remove the Read
	  Only attribute.
	
	  To remove the Read Only attribute, use the instructions below for your version
	  of Windows:
	
	  Windows 3.x and Windows NT
	
	  a. Start Windows File Manager.
	
	  b. In the C:\Winword\Startup folder, select the Bshelf94.dot file.
	
	  c. From the File menu, choose Properties.
	
	  d. In the Attributes section, clear the Read-Only check box.
	
	  e. Choose OK.
	
	  f. Repeat steps b through e for C:\Windows\System\Bookshlf.dll and
	     C:\Books94\Bsword.hlp.
	
	  Windows 95
	
	  a. With your right mouse button, click on the Start button, and then click
	     Explore
	
	  b. Click the Startup folder in the C:\Winword folder
	
	  c. With your right mouse button, click the Bshelf94.dot file, and then click
	     Properties.
	
	  d. Clear the box for the Read-Only attribute, and then click OK.
	
	5. Use a text editor to add the following entries to the [Bookshelf] section of
	  the WIN.INI file:
	
	        [Bookshelf]
	        Integration=2
	        LastQuote=1
	        BSWordHelp=C:\Books94\Bsword.hlp
	
	  Word now contains an option on the View menu for Quote of the Day. To access
	  Bookshelf from Word, use QuickShelf. The Copy to Word function appear on
	  Bookshelf's Edit menu.
	
	6. If you are integrating Bookshelf with Word 6.0, the process is complete. If
	  you are integrating Bookshelf with Word 2.0, do the following.
	
	  NOTE: The steps below are for Word 2.0 only:
	
	  a. Start Microsoft Word.
	
	  b. On the File menu, click Open, and then double-click the Startup folder.
	
	  c. Type the following in the filename Edit Box, and press ENTER:
	
	  "bshelf94.dot" (without the quotation marks)
	
	  d. On the Tools menu, click Macros.
	
	  e. Click Template Macros.
	
	  f. Select wabSetup and choose Run.
	
	  g. Exit Word and when you are asked if you want to save global glossary and
	     command changes, click Yes.
	
	Additional query words: kbhowto 1994 multi media multimedia multi-media mmtitles kbmm
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeMMsearch kbBookshelfSearch kbBookShelf1994
	Version           : :1994 edition
	
	=============================================================================
	

{% endraw %}
