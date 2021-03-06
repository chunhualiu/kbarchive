---
layout: page
title: "Q33032: &quot;Field Overflow&quot; Using INPUT, ON ERROR to Set Record"
permalink: /kb/033/Q33032/
---

## Q33032: &quot;Field Overflow&quot; Using INPUT, ON ERROR to Set Record

{% raw %}

	Article: Q33032
	Product(s): See article
	Version(s): 4.00 4.00b 4.50
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | buglist4.00 buglist4.00b fixlist4.50 B_BasicCom | mspl13_basic
	Last Modified: 6-DEC-1989
	
	In the program below, using an ON ERROR trapping routine to correctly
	set the record length for a random file continually returns a "field
	overflow" error message.
	
	To work around this problem, initially use the correct record-length
	value.
	
	Microsoft has confirmed this to be a problem in Microsoft QuickBASIC
	Versions 4.00 and 4.00b, and the Microsoft BASIC Compiler Versions
	6.00 and 6.00b for MS-DOS and MS OS/2 (buglist6.00, buglist6.00b).
	This problem has been corrected in QuickBASIC Version 4.50 and in the
	Microsoft BASIC Compiler Version 7.00 (fixlist7.00).
	
	The following program will continually return a "field overflow" error
	message:
	
	   COMMON SHARED c
	   ON ERROR GOTO trap
	   CLS
	   OPEN "foofile" FOR RANDOM AS #1 LEN = 5
	   FIELD #1, 5 AS a$
	   b$ = "hello"
	   LSET a$ = b$
	   PUT #1, 1
	   c = 6
	   get$ = INPUT$(c, #1)
	   print c
	   PRINT get$
	   END
	   trap:
	     PRINT ERR
	     c = 5
	     RESUME

{% endraw %}
