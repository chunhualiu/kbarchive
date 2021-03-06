---
layout: page
title: "Q38809: Error L1085 Cannot Open Temporary File"
permalink: /kb/038/Q38809/
---

## Q38809: Error L1085 Cannot Open Temporary File

{% raw %}

	Article: Q38809
	Product(s): See article
	Version(s): 5.00 5.10 | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | s_pascal h_fortran h_masm s_quickc s_link s_error | mspl13_c
	Last Modified: 7-DEC-1988
	
	The following error is from "Linker Error Messages" in the manual
	"CodeView and Utilities," Section C.2, Page 364, and in the "Microsoft
	QuickC Compiler Programmer's Guide," Section D.4, Page 370:
	
	L1085       cannnot open temporary file
	
	            The disk or the root directory was full.
	
	            Delete or move files to make space.
	
	Fatal errors cause the linker to stop execution. Fatal error messages
	have the following format:
	
	   location : fatal error L1xxx: messagetext
	
	In these messages, location is the input file associated with the
	error, or LINK if there is no input file. If the input file is an OBJ
	or LIB file and has a module name, the module name is enclosed in
	parentheses.
	
	This error can be caused by insufficient file handles. Resident
	software (TSR) can use up some handles, or can cause other kinds of
	interference that can cause this error.

{% endraw %}
