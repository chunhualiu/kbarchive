---
layout: page
title: "Q31143: Return Type for ReadCmd Is PSWI, Not PCMD"
permalink: /kb/031/Q31143/
---

## Q31143: Return Type for ReadCmd Is PSWI, Not PCMD

{% raw %}

	Article: Q31143
	Product(s): See article
	Version(s): 1.00 | 1.00
	Operating System(s): OS/2 | MS-DOS
	Keyword(s): ENDUSER | docerr | mspl13_basic
	Last Modified: 12-JAN-1989
	
	Page 7 of the EXT.DOC file, located in the SOURCE\ME\EXT directory of
	the Microsoft C Optimizing Compiler Version 5.10, incorrectly lists
	the return type for the ReadCmd command as being PCMD.
	
	The correct return type is PSWI, which is documented in the EXT.H
	file.

{% endraw %}
