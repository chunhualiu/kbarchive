---
layout: page
title: "Q61105: End User Made Mouse Menus Don't Run Under MS-DOS 4.00 or 4.01"
permalink: /kb/061/Q61105/
---

## Q61105: End User Made Mouse Menus Don't Run Under MS-DOS 4.00 or 4.01

{% raw %}

	Article: Q61105
	Product(s): See article
	Version(s): 1.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 20-JUN-1990
	
	Mouse menus compiled with MAKEMENU.EXE and run with the MENU.COM that
	came with Mouse driver versions 6.24b and earlier will not work under
	MS-DOS version 4.00 or 4.01. The menu will install into memory, but
	will not be visible and will not interface correctly with the
	application.
	
	Currently, the only workaround is to load the ANSI.SYS driver with the
	/k option. This disables the extended keys on the keyboard, which
	allows your Mouse menus to work.
	
	Microsoft is researching this problem and will post new information
	as it comes available.

{% endraw %}
