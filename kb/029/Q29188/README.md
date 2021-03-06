---
layout: page
title: "Q29188: Unresolved External on &#95;&#95;Clpow with /Oi and /FPa in C 5.xx"
permalink: /kb/029/Q29188/
---

## Q29188: Unresolved External on &#95;&#95;Clpow with /Oi and /FPa in C 5.xx

{% raw %}

	Article: Q29188
	Product(s): See article
	Version(s): 5.00 5.10
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 15-JAN-1991
	
	The C version 5.00 and 5.10 compilers generate an unresolved external
	reference to __CIpow when the sample program below is compiled with
	/Oi (or /Ox) and /FPa.
	
	Intrinsic optimization (/Oi) and the alternate floating-point option
	are not compatible and cannot be used together. This restriction is
	noted in the C 5.10 README.DOC. The maximum optimization that you can
	use with the alternate floating-point option is /Oalt.
	
	Sample Code
	-----------
	
	   /* Compile with /Oi and /FPa  */
	
	   #include <math.h>
	   #include <stdio.h>
	
	   main()
	   {
	   float  xx, yy;
	   xx = 4.7;
	   yy = 3.9;
	   printf("%f", pow(xx,yy));
	   }

{% endraw %}
