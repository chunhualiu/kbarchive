---
layout: page
title: "Q51835: &quot;Error C2410: 'var' : Ambiguous Member Name Operand 2&quot;"
permalink: /kb/051/Q51835/
---

## Q51835: &quot;Error C2410: 'var' : Ambiguous Member Name Operand 2&quot;

{% raw %}

	Article: Q51835
	Product(s): See article
	Version(s): 2.00 2.01
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | buglist2.01 | mspl13_c
	Last Modified: 14-MAR-1990
	
	The following code generates the following error:
	
	   file.c(x) : error c2410: 'var' : ambiguous member name operand 2
	
	Code Example
	------------
	
	void main (void)
	{
	     struct tag1
	     {
	          int  member;   <---|
	     } name1;                |
	                             |---- two different structures with
	     struct tag2             |     same member name
	     {                       |
	          int  member;   <---|
	     } name2;
	
	     _asm      mov  bx, name2.member;
	}
	
	The compiler is confused by the two members with the same name.
	However, this behavior is observed only when referencing the structure
	member in an in-line assembly statement. If the member is referenced
	in a C statement, no error will occur. The only current workaround is
	to have different member names.
	
	Microsoft has confirmed this to be a problem in QuickC Version 2.10.
	We are researching this problem and will post new information here as
	it becomes available.

{% endraw %}
