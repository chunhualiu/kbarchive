---
layout: page
title: "Q241810: BUG: IDispEventImpl Event Handlers May Give Strange Parameters"
permalink: /kb/241/Q241810/
---

## Q241810: BUG: IDispEventImpl Event Handlers May Give Strange Parameters

{% raw %}

	Article: Q241810
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbActivexEvents kbCOMt kbConnPts kbVC600bug kbATL300bug kbDSupport kbGrpDSMFCATL
	Last Modified: 28-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Active Template Library (ATL) 3.0, included with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When using IDispEventImpl in a client that is sinking events with parameters
	that have different data types with different sizes, the handlers of the events
	will get incorrect values for the event parameters. The following sample IDL
	code will cause problems when sinking the event in an ATL client.
	
	  [//attributes omitted for brevity.
	  ]
	  dispinterface _ISomeEvents
	  {
	    properties:
	    methods:
	    [id(1), helpstring("method Event1")] HRESULT Event1([in] short s, [in] double d);
	  };
	
	CAUSE
	=====
	
	The cause is errors in the GetFuncInfoFromId() function in the IDispEventImpl
	class, which is located in Atlcom.h.
	
	The following code (in Atlcom.h, line 3918) is in error:
	
	  for (int i=0; i<pFuncDesc->cParams; i++)
	  {
	    info.pVarTypes[i] = pFuncDesc->lprgelemdescParam[pFuncDesc->cParams - i - 1].tdesc.vt;
	    if (info.pVarTypes[i] == VT_PTR)
	       info.pVarTypes[i] = pFuncDesc->lprgelemdescParam[pFuncDesc->cParams - i - 1].tdesc.lptdesc->vt | VT_BYREF;
	    if (info.pVarTypes[i] == VT_USERDEFINED)
	       info.pVarTypes[i] = GetUserDefinedType(spTypeInfo,pFuncDesc->lprgelemdescParam[pFuncDesc->cParams-i-1].tdesc.hreftype);
	  }
	
	The code should instead be:
	
	  for (int i=0; i<pFuncDesc->cParams; i++)
	  {
	    info.pVarTypes[i] = pFuncDesc->lprgelemdescParam[i].tdesc.vt;
	    if (info.pVarTypes[i] == VT_PTR)
	       info.pVarTypes[i] = pFuncDesc->lprgelemdescParam[i].tdesc.lptdesc->vt | VT_BYREF;
	    if (info.pVarTypes[i] == VT_USERDEFINED)
	       info.pVarTypes[i] = GetUserDefinedType(spTypeInfo,pFuncDesc->lprgelemdescParam[i].tdesc.hreftype);
	  }
	
	RESOLUTION
	==========
	
	Workarounds
	-----------
	
	There are three workarounds for this problem:
	
	- Provide the type information for the sink method by using the
	  SINK_ENTRY_INFO() macro instead of SINK_ENTRY() or SINK_ENTRY_EX(). For
	  additional information on how to use this macro, click the article number
	  below to view the article in the Microsoft Knowledge Base:
	
	  Q194179 SAMPLE: AtlEvnt.exe Creates ATL Sinks Using IDispEventImpl
	
	
	- Override the virtual function GetFuncInfoFromId() in your
	  IDispEventImpl-derived class. The new function should be identical to the
	  original except for the five altered lines in the code shown in the Cause
	  section of this article.
	
	- Change the incorrect code in Atlcom.h for the
	  IDispEventImpl::GetFuncInfoFromId() function:
	
	  1. Copy the file Atlcom.h in your project directory and name it
	     "Atlcom-fix.h" (without the quotation marks).
	
	  2. Change the reference to Atlcom.h in StdAfx.h to Atlcom-fix.h.
	
	  3. In Atlcom-fix.h, change the code for the
	     IDispEventImpl::GetFuncInfoFromId() function as described in the Cause
	     section of this article.
	
	  4. Save Atlcom-fix.h.
	
	  5. From the Build menu, select, Rebuild All. Do this on a Debug or
	     ReleaseMinDependency build so that the modified code described previously
	     will be linked into your code.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	REFERENCES
	==========
	
	Documentation for IDispEventImpl in MSDN
	
	  Q194179 SAMPLE: AtlEvnt.exe Creates ATL Sinks Using IDispEventImpl
	
	Additional query words: bad parms parameters stack order backwards sink event SINK_ENTRY_INFO SINK_ENTRY_EX SINK_ENTRY
	
	======================================================================
	Keywords          : kbActivexEvents kbCOMt kbConnPts kbVC600bug kbATL300bug kbDSupport kbGrpDSMFCATL 
	Technology        : kbVCsearch kbAudDeveloper kbATLsearch
	Version           : WINDOWS:3.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
