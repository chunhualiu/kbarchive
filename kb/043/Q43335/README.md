---
layout: page
title: "Q43335: cegal() Function in EGA.LIB May Not Work Properly"
permalink: /kb/043/Q43335/
---

## Q43335: cegal() Function in EGA.LIB May Not Work Properly

{% raw %}

	Article: Q43335
	Product(s): See article
	Version(s): 1.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | | mspl13_basic
	Last Modified: 16-APR-1990
	
	When using cegal() in the EGA.LIB with Function f1, cegal() doesn't
	perform correctly. An example is shown below.
	
	Perform the following function in C
	
	   outp(CRTC_INDEX,INDEX);
	
	where CRTC_INDEX is the port address and INDEX is the register.
	
	The mouse will not see the change in the EGA register; therefore, the
	above C call may cause the mouse to not perform properly because the
	call bypasses the BIOS routines.
	
	The following are two ways to perform this call so that the mouse will
	see the change in the EGA register:
	
	1. Use the EGA.LIB (this does not work):
	
	         e1=0xf1;
	         e2=0xd;
	         e4=0;
	         cegal(&e1,&e2,&e3,&e4,&e5);
	
	2. Use the equivalent BIOS call (this works):
	
	         inregs.x.ax=0xf1;
	         inregs.x.bx=0xd;
	         inregs.x.dx=0;
	         int86(0x10,&inregs,&outregs);

{% endraw %}
