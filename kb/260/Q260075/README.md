---
layout: page
title: "Q260075: PRB: Server Stops Responding When You Call MTS Under ASP"
permalink: /kb/260/Q260075/
---

## Q260075: PRB: Server Stops Responding When You Call MTS Under ASP

{% raw %}

	Article: Q260075
	Product(s): Internet Information Server
	Version(s): WINDOWS:6.0; winnt:4.0
	Operating System(s): 
	Keyword(s): kbMTS kbVBp600 kbWinDNA kbGrpDSSIE kbScalability kbDSupport kbiis400
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server 4.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you call a Microsoft Transaction Server (MTS) component from a
	non-Microsoft Transaction Server component that is
	
	- running under Microsoft Active Server Pages (ASP)
	
	-and-
	
	- written in Microsoft Visual Basic
	
	then your server may stop responding to ASP requests when it is placed under
	stress.
	
	CAUSE
	=====
	
	This behavior can happen if the calling component creates the second component
	through the use of CreateObject, instead of through the object context's
	CreateInstance method.
	
	A call to Server.CreateObject always creates an MTS thread with a context
	wrapper. Therefore, the first object is created on an MTS thread and ends up
	creating a second object, which is an MTS object. CreateInstance should be used
	when you create an MTS object from an object in Microsoft Transaction Server.
	
	Another way to avoid this problem is to configure the calling component into an
	MTS server package so that it will start in a different process than if it were
	created in Inetinfo.exe's process space.
	
	RESOLUTION
	==========
	
	Because the calling component is running under ASP, it has access to all of the
	ASP properties and methods. Instead of creating the component using
	CreateObject, you can use the CreateInstance property of the ObjectContext
	object. For an example of how to accomplish this, see the example in the "More
	Information" section.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new ActiveX DLL project in Visual Basic.
	
	2. Rename the project from "Project1" to "NotAnMTSComponent" (without the
	  quotation marks).
	
	3. Rename "Class1" to "CNotAnMTSComponent" (without the quotation marks).
	
	4. Paste the following code into cNotAnMTSComponent:
	
	  Option Explicit
	
	  Public Sub Test()
	
	      Dim x As Object
	      
	      Set x = CreateObject("MyMTSComponent.cMTSComponent")
	      x.DoSomething
	      Set x = Nothing
	      
	      
	  End Sub
	
	5. From the Visual Basic File menu, select Add Project, and create a new ActiveX
	  DLL.
	
	6. Rename the project from "Project1" to "MyMTSComponent" (without the quotation
	  marks).
	
	7. Rename "Class1" to "cMTSComponent" (without the quotation marks).
	
	8. Set the MTSTransactionMode of cMTSComponent to 2 - Requires Transaction.
	
	9. From the Project menu, select References, and add a reference to "Microsoft
	  Transaction Server Type Library" (without the quotation marks).
	
	10. Paste the following code into cMTSComponent:
	
	  Option Explicit
	
	  Public Sub DoSomething()
	
	      Dim oc As ObjectContext
	      Dim x  As Integer
	      Dim strNothing As String
	      
	      
	      Set oc = GetObjectContext
	      
	      'Waste some time here
	      For x = 1 To 1000
	          strNothing = strNothing + String(1000 * Rnd() + 1, " ")
	      Next x
	          
	      
	      oc.SetComplete
	      Set oc = Nothing
	      
	
	  End Sub
	
	11. Compile both .dll files.
	
	12. Use your MTS Explorer to create a new package, and then add
	  MyMTSComponent.dll to the package.
	
	13. Create an ASP page named "Test.asp" (without the quotation marks). Paste the
	  following code into it:
	
	  <%@ LANGUAGE = VBScript %>
	  <html>
	  <body>
	  <%
	       dim myObj
	       set myObj = SErver.CreateObject("NotAnMTSComponent.cNotAnMTSComponent")
	
	  %>
	
	  Done!
	  </body>
	  </html>
	
	14. Use the Internet Services Manager to create a new application. Make its path
	  C:\Inetpub\Wwwroot\Test. (Modify the path as necessary to suit your Internet
	  Information Services [IIS] setup.) Ensure that the application is running in
	  a separate process. Name the application "Test" (without the quotation
	  marks).
	
	15. Put Test.asp into C:\Inetpub\Wwwroot\Test.
	
	16. Use a Web application stress tool (for example,
	  http://webtool.rte.microsoft.com/) to apply a load to your Web site. Your
	  application should stop responding ("hang").
	
	To solve the problem, change the code in cNotAnMTSComponent to:
	
	  Option Explicit
	
	  Public Sub Test()
	
	      Dim x As Object
	      Dim oc as ObjectContext
	
	      Set oc = GetObjectContext
	      Set x = oc.CreateInstance("MyMTSComponent.cMTSComponent")
	      x.DoSomething
	      Set x = Nothing
	      set oc = nothing
	      
	  End Sub
	
	REFERENCES
	==========
	
	Ted Pattison provides good information on this topic in his book Programming
	Distributed Applications with COM and Microsoft(r) Visual Basic(r) 6.0 (pages
	284-288) and in "Creating Objects Properly in an MTS App" in the August 1999
	edition of the Microsoft Independent Developer.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbMTS kbVBp600 kbWinDNA kbGrpDSSIE kbScalability kbDSupport kbiis400 
	Technology        : kbVBSearch kbiisSearch kbAudDeveloper kbZNotKeyword6 kbiis400 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600
	Version           : WINDOWS:6.0; winnt:4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
