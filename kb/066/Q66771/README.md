---
layout: page
title: "Q66771: How to Re-create BASIC Help Files Using HELPMAKE.EXE"
permalink: /kb/066/Q66771/
---

## Q66771: How to Re-create BASIC Help Files Using HELPMAKE.EXE

{% raw %}

	Article: Q66771
	Product(s): See article
	Version(s): 7.00 7.10
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | SR# S901105-139 | mspl13_basic
	Last Modified: 8-NOV-1990
	
	HELPMAKE.EXE is designed to allow you to decode/encode the Help files
	included with BASIC PDS, and to create your own Help files for use
	with BASIC, QuickHelp, and other products that use these files.
	
	This information applies to Microsoft BASIC Professional Development
	System (PDS) versions 7.00 and 7.10 for MS-DOS and MS OS/2.
	
	To decode a BASIC Help file, use the following command:
	
	   HELPMAKE /D <HelpFileName> /O<OutputFile>
	
	You may now modify (customize) the decoded Help file.
	
	To re-encode the Help file after you have edited it, use the following
	command:
	
	   HELPMAKE /E <SourceFile> /A: /T /W78 /O<HelpFileName>
	
	The options on the above encode line are explained below:
	
	  /E   Encode the file. /E with no value gives the maximum
	       compression. /E may optionally be followed by a value
	       specifying the amount of compression to use:
	
	           0 - No Compression
	           1 - Run-length compression
	           2 - Keyword compression
	           4 - Extended keyword compression
	           8 - Huffman compression
	
	       These values may be added together to combine compression
	       types. For example, /E5 will generate Run-length and Extended
	       keyword compression.
	
	  /A:  Specifies a colon as the control character. This is the default
	       value so it may be omitted.
	
	  /T   Translates dot commands. This is required to re-encode the
	       BASIC Help files.
	
	  /W78 Specifies the width of the resulting Help file. BASIC uses a
	       width of 78 characters. The default is 76 so this option must
	       be included.
	
	For a more detailed discussion of HELPMAKE, refer to Chapter 11 of
	"Microsoft BASIC 7.0: Programmer's Guide" for versions 7.00 and 7.10.

{% endraw %}
