---
layout: page
title: "Q135765: PRB: Convert Dialog Doesn't Appear for OLE Object in MS Excel"
permalink: /kb/135/Q135765/
---

## Q135765: PRB: Convert Dialog Doesn't Appear for OLE Object in MS Excel

{% raw %}

	Article: Q135765
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kbole kbCOMt kbMFC kbVC kbVS97 kbVS600 kbGrpDSMFCATL
	Last Modified: 02-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, versions 1.5, 1.51, 1.52 
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, versions 2.0, 2.1, 2.2, 4.0, 4.1 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When the Edit|<Object>|Convert... menu item is selected for an OLE object
	that is embedded within a Microsoft Excel document, the Convert dialog box does
	not appear.
	
	CAUSE
	=====
	
	Microsoft Excel displays the Convert dialog for an object only if
	WriteFmtUserTypeStg has been used to write out a clipboard format and
	user-readable name for the contents of the object. The MFC libraries do not call
	this function when creating or saving OLE objects.
	
	
	RESOLUTION
	==========
	
	Call WriteFmtUserTypeStg in the Serialize method of your server's document
	class.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	WriteFmtUserTypeStg should be called as part of your server's implementation of
	IPersistStorage::InitNew and IPersistStorage::Save. By default, MFC OLE server
	applications do not call WriteFmtUserTypeStg in their implementation of
	IPersistStorage::InitNew and IPersistStorage::Save. One simple way to achieve
	this functionality in an MFC application is to make the call to
	WriteFmtUserTypeStg in the Serialize method of the server's document class.
	
	Steps to Add a Call to WriteFmtUserTypeStg
	------------------------------------------
	
	1. Provide a private clipboard format for your object.
	
	  WriteFmtUserTypeStg serializes a clipboard format and user-readable name for
	  the contents of an object to its storage. The HIERSVR sample shows how to
	  provide a private clipboard format for your object if you do not already have
	  one.
	
	2. Add the DoWriteFmtUserTypeStg helper function to your document class.
	
	  This helper function is used to encapsulate retrieving the clipboard format
	  and user-readable name when calling WriteFmtUserTypeStg. The code in the
	  "Sample Code" section of this article shows how to implement this function
	  for the HIERSVR sample.
	
	3. Modify the server document's Serialize() method and add a call to the
	  DoWriteFmtUserTypeStg helper function, as shown in the following sample code.
	
	Sample Code
	-----------
	
	     void CServerDoc::DoWriteFmtUserTypeStg(LPSTORAGE lpStorage)
	     {
	        LPOLEOBJECT lpObject = (LPOLEOBJECT)GetInterface(&IID_IOleObject);
	        ASSERT(lpObject != NULL);
	        CLSID clsid;
	        lpObject->GetUserClassID(&clsid);
	
	        LPTSTR pszUserType = NULL;
	        OleRegGetUserType(clsid, USERCLASSTYPE_FULL, (LPOLESTR
	     *)&pszUserType);
	
	        if (pszUserType)
	        {
	           WriteClassStg(lpStorage, clsid);
	           WriteFmtUserTypeStg(lpStorage, m_cfPrivate,
	     (LPOLESTR)pszUserType);
	           CoTaskMemFree(pszUserType);
	        }
	     }
	
	     void CServerDoc::Serialize(CArchive& ar)
	     {
	       ASSERT(m_pRoot != NULL);
	
	       if(IsEmbedded() && ar.IsStoring())
	       {
	         ASSERT(m_lpRootStg != NULL);
	         DoWriteFmtUserTypeStg(m_lpRootStg);
	       }
	
	       SerializeFontInfo(ar);
	       m_pRoot->Serialize(ar);
	     }
	
	Additional query words: alwaysupdate
	
	======================================================================
	Keywords          : kbole kbCOMt kbMFC kbVC kbVS97 kbVS600 kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
