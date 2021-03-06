---
layout: page
title: "Q168003: FIX: Function Prototypes in comutil.h Missing Calling Convention"
permalink: /kb/168/Q168003/
---

## Q168003: FIX: Function Prototypes in comutil.h Missing Calling Convention

{% raw %}

	Article: Q168003
	Product(s): Microsoft C Compiler
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): kbcode kbVC500bug kbVS97sp1fix
	Last Modified: 17-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	- Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Unresolved external errors may occur when you compile with a default calling
	convention of __fastcall (/Gr) or __stdcall (/Gz) and call ConvertStringToBSTR
	or ConvertBSTRToString.
	
	CAUSE
	=====
	
	The prototypes are missing the __cdecl calling convention, which is the calling
	convention of these functions in comsupp.lib.
	
	RESOLUTION
	==========
	
	Build with __cdecl as the default calling convention. Do not build with
	__fastcall or __stdcall as the default calling convention.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been corrected in Visual Studio 97
	Service Pack 1.
	
	For additional information about the Visual Studio 97 Service Pack 1, please see
	the following article in the Microsoft Knowledge Base:
	
	  Q170365 INFO: Visual Studio 97 Service Packs - What, Where, and Why
	
	MORE INFORMATION
	================
	
	Sample Code
	-----------
	
	     //compile options needed: /Gr or /Gz
	     #include <comutil.h>
	     int main()
	     {
	         char sz[]="hello";
	         _bstr_t b;
	         b = _com_util::ConvertStringToBSTR(sz);
	         char * p = _com_util::ConvertBSTRToString(b);
	         return 1;
	     }
	
	The following linker errors occur when you compile this sample code:
	
	  
	
	  error LNK2001: unresolved external symbol "char * __fastcall
	  _com_util::ConvertBSTRToString(unsigned short *)"
	  (?ConvertBSTRToString@_com_util@@YIPADPAG@Z)
	
	  
	
	  error LNK2001: unresolved external symbol "unsigned short * __fastcall
	  _com_util::ConvertStringToBS
	  TR(char const *)" (?ConvertStringToBSTR@_com_util@@YIPAGPBD@Z)
	
	Additional query words: LNK2001
	
	======================================================================
	Keywords          : kbcode kbVC500bug kbVS97sp1fix 
	Technology        : kbVCsearch kbAudDeveloper kbVC500 kbVC32bitSearch kbVC500Search
	Version           : 5.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
