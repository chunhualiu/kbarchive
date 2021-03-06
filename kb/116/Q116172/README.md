---
layout: page
title: "Q116172: BUG: Based Ptr. Init Fails at Global Scope in CPP File"
permalink: /kb/116/Q116172/
---

## Q116172: BUG: Based Ptr. Init Fails at Global Scope in CPP File

{% raw %}

	Article: Q116172
	Product(s): Microsoft C Compiler
	Version(s): 1.0,1.5,2.0,4.0,4.1,4.2
	Operating System(s): 
	Keyword(s): kbCompiler kbCPPonly kbVC
	Last Modified: 11-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C/C++ Compiler (CL.EXE), used with:
	   - Microsoft C/C++ for MS-DOS 
	   - Microsoft Visual C++ for Windows, 16-bit edition, versions 1.0, 1.5 
	   - Microsoft Visual C++, 32-bit Editions, versions 1.0, 2.0, 4.0, 4.1, 4.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When attempting to compile an application written in C++ that contains a based
	pointer initialized at global scope, the compiler incorrectly returns the error
	message
	
	  error C2440 : 'initializing' : cannot convert from 'int __far *' to 'int
	  __based(xxxx) *'
	
	where xxxx is the segment on which the pointer is based.
	
	This error does not occur for based pointers that are initialized at function
	scope.
	
	RESOLUTION
	==========
	
	Sample Code 1
	-------------
	
	With the 16-bit compilers listed above, this error can be eliminated by
	typecasting the constant that is used to initialize the based pointer to a type
	"_based(void) *". The following code demonstrates how to generate the compiler
	error as well as the workaround:
	
	  /* Compile options needed:   none
	  */ 
	
	  // Base Pointer
	  int *BasePtr;
	
	  // This line compiles fine (no initialization)
	  int _based(BasePtr) *test1;
	
	  // This line generates an C2440 error
	  int _based(BasePtr) *test2=0;
	
	  // This line demonstrates the 16 bit workaround
	  int _based(BasePtr) *test3 = (int _based(void) *)0;
	
	  void main(void)
	  {
	  // Initialization at file scope does not generate C2440
	
	     int _based(BasePtr) *test4 = 0;
	  }
	
	Sample Code 2
	-------------
	
	In the 32-bit compiler for Windows NT, version 8.0, the workaround given for the
	16-bit compilers does not work. The "_based(void) *" cast generates the
	following two error messages if you are using the 32-bit compiler:
	
	  error C2493: illegal form of __based error C2440: 'initializing' : cannot
	  convert from 'int *' to 'int __based(BasePtr) *'
	
	In this case, the file scope based pointer cannot be declared and initialized in
	one step. An appropriate workaround would be to declare the pointer at file
	scope and initialize the pointer inside of a function. The following code
	demonstrates how to generate the compiler error as well as the workaround:
	
	  /* Compile options needed: none
	  */ 
	  // Base Pointer
	  int *BasePtr;
	
	  // This line compiles fine (no initialization).
	  int _based(BasePtr) *test1;
	
	  // This line generates C2440 error.
	  int _based(BasePtr) *test2=0;
	
	  // This line generates C2440 and C2493 errors.
	  int _based(BasePtr) *test3 = (int _based(void) *)0;
	
	  void main(void)
	  {
	  // 32-bit workaround: initialize the based pointer at function scope.
	
	     test1 = 0;
	
	  // Initialization at file scope does not generate C2440 or C2493.
	
	     int _based(BasePtr) *test4 = 0;
	  }
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	Additional query words: kbVC400bug 8.00 8.00c 9.00
	
	======================================================================
	Keywords          : kbCompiler kbCPPonly kbVC 
	Technology        : kbVCsearch kbAudDeveloper kbCVCComp
	Version           : :1.0,1.5,2.0,4.0,4.1,4.2
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
