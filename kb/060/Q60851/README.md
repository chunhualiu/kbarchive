---
layout: page
title: "Q60851: TSCNIOxx.OBJ Stub Files Remove COLOR Border Parameter"
permalink: /kb/060/Q60851/
---

## Q60851: TSCNIOxx.OBJ Stub Files Remove COLOR Border Parameter

{% raw %}

	Article: Q60851
	Product(s): See article
	Version(s): 7.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | SR# S900327-66 | mspl13_basic
	Last Modified: 20-APR-1990
	
	When a Microsoft BASIC Professional Development System (PDS) Version
	7.00 program is linked with one of the TSCNIOxx.OBJ stub files, most
	graphics statements and functions are stubbed out. When a program that
	has been linked in this manner attempts to use the "border" parameter
	syntax of the COLOR statement, the run-time error "Feature
	unavailable" should be generated. This is because the border parameter
	syntax support is contained in the graphics portion of the BASIC
	run-time module and this is removed, or stubbed, during LINK time.
	
	The syntax for the COLOR statement that applies here is as follows:
	
	   COLOR [foreground][,background][,border]
	
	This statement is only supported on a CGA graphics adapter in SCREEN 0.

{% endraw %}
