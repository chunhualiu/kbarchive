---
layout: page
title: "Q35025: Accessing Switch Values in C Extensions"
permalink: /kb/035/Q35025/
---

## Q35025: Accessing Switch Values in C Extensions

{% raw %}

	Article: Q35025
	Product(s): See article
	Version(s): 1.00   | 1.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 2-SEP-1988
	
	There is no direct function call to access switch values defined in
	the editor, such as rmargin or vscroll or hike, in your C Extension.
	However, you can find the value by using fExecute() to switch to the
	help file, then use the psearch or msearch functions to locate
	rmargin. At the end of that line you will find the value associated
	with rmargin.
	
	The following is an example:
	
	fExecute("Arg \"<assign>\" Setfile");  /* switch to "<assign>" file   */
	fExecute("Mark");                      /* go to beginning of it       */
	fExecute("Arg \"rmargin\" Psearch");   /* search for "rmargin"        */
	fExecute("Pword");                     /* get the number after it     */
	
	You also can use the GetLine() function to read through the <assign>
	file; this method involves more coding, but it will run faster than
	using fExecute() to execute macros.

{% endraw %}
