---
layout: page
title: "Q66345: BSEDOS.H in C 6.00 Has Incorrect Prototypes"
permalink: /kb/066/Q66345/
---

## Q66345: BSEDOS.H in C 6.00 Has Incorrect Prototypes

{% raw %}

	Article: Q66345
	Product(s): See article
	Version(s): 6.00 6.00a
	Operating System(s): OS/2
	Keyword(s): ENDUSER | buglist6.00 buglist6.00a | mspl13_c
	Last Modified: 21-JAN-1991
	
	The prototypes for DosPeekQueue() and DosFileLocks() in the BSEDOS.H
	file are incorrect.
	
	The fourth parameter for DosPeekQueue() is defined in the header file
	as being of type PULONG, as shown in the following:
	
	   PULONG ppBuf
	
	For OS/2 versions 1.x, the fourth parameter should be as follows:
	
	   PVOID FAR *ppBuf
	
	The prototype is correct as it is for OS/2 version 2.00.
	
	For OS/2 versions 1.x, the second and third parameters for
	DosFileLocks() are defined as being of type PLONG, and should be of
	type PFILELOCK.
	
	This function does not exist in OS/2 version 2.00.
	
	Microsoft has confirmed this to be a problem in C versions 6.00 and
	6.00a. We are researching this problem and will post new information
	here as it becomes available.

{% endraw %}
