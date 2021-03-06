---
layout: page
title: "Q221720: FIX: COM Servers Cannot Redimension Arrays Passed By Reference"
permalink: /kb/221/Q221720/
---

## Q221720: FIX: COM Servers Cannot Redimension Arrays Passed By Reference

{% raw %}

	Article: Q221720
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbCOMt kbvfp500aBUG kbvfp600bug kbVS600sp3fix kbGrpDSFox kbDSupport
	Last Modified: 14-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You pass an array by reference to a method of a COM server built in Visual
	FoxPro. The method redimensions the array. If you call the method from a Visual
	FoxPro 6.0 client and use the COMARRAY function, you may see the following
	error:
	
	  OLE IDispatch exception code 302 from Visual FoxPro for Windows: Data type
	  mismatch...
	
	If you call the method from a Visual FoxPro 5.0 client, or a Visual FoxPro 6.0
	client not using the COMARRAY function, you may not see an error, but instead
	the array will not be redimensioned, and the array's original contents remain
	unchanged. From clients other than Visual FoxPro, you may see the earlier
	behaviors, or other variations.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	This bug has been fixed in Visual Studio 6.0 Service Pack 3.
	
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new project called Arraytest.
	
	2. Add a new program to the project.
	
	3. Paste the following code into the program:
	
	     DEFINE CLASS arraydim AS CUSTOM OLEPUBLIC
	        cVerStr = VERSION()
	        PROCEDURE GetArray(taArray, tnRows)
	           IF PARAMETERS() < 2
	              tnRows = ALEN(taArray)
	           ENDIF
	           LOCAL lni
	           DIMENSION taArray[tnRows]
	           FOR lni = 1 TO ALEN(taArray)
	              taArray[lni] = lni
	           ENDFOR
	           RETURN
	        ENDPROC
	     ENDDEFINE
	
	4. Save the program as Arraytest.prg.
	
	5. Build the project into a COM DLL.
	
	6. Run the following code from a program (.prg) file:
	
	     CLEAR
	     CLEAR ALL
	     LOCAL ARRAY laArray[5]
	     LOCAL OX
	     ox = CREATEOBJECT('arraytest.arraydim')
	     * =COMARRAY(ox,11)
	     STORE 'X' to laArray
	     ?'Value of first element',laArray[1]
	     ?'Array length before', ALEN(laArray)
	     ox.GetArray(@laArray, 10)
	     RELEASE ox
	     ?'Array length after', ALEN(laArray)
	     ?'Value of first element',laArray[1]
	
	7. From a Visual FoxPro 5.0 client (this must be done with the COMARRAY function
	  removed) the array length and value of the first element are unchanged. From
	  a Visual FoxPro 6.0 client, using the COMARRAY function, the error listed in
	  SYMPTOMS will occur. From a Visual FoxPro 6.0 client not using the COMARRAY
	  function, the behavior is the same as that under Visual FoxPro 5.0.
	
	REFERENCES
	==========
	
	Visual FoxPro Help, COMARRAY() topic.
	
	(c) Microsoft Corporation 1999, All Rights Reserved. Contributions by Jim
	Saunders, Microsoft Corporation.
	
	
	Additional query words:
	
	======================================================================
	Keywords          : kbCOMt kbvfp500aBUG kbvfp600bug kbVS600sp3fix kbGrpDSFox kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:5.0,5.0a,6.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
