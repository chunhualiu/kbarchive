---
layout: page
title: "Q149057: INFO: Understanding Dynamic Resultset Cursors -RDO"
permalink: /kb/149/Q149057/
---

## Q149057: INFO: Understanding Dynamic Resultset Cursors -RDO

{% raw %}

	Article: Q149057
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses some advanced topics regarding RDO Dynamic cursors that
	are not explained in the Visual Basic documentation. Use it as a supplement to
	Understanding Cursors and Choosing a Cursor Type found in the Visual Basic
	online Help by doing an indexed find on the keyword Cursors.
	
	Use the Visual Basic online Help and the Building Client/Server Applications
	guide to get more general information on the different types of RDO cursors.
	
	
	MORE INFORMATION
	================
	
	Dynamic cursors have no fixed membership of rows. As you move from one rowset to
	another (number of rows in a rowset is determined by the RowsetSize property),
	the driver may return any set of rows. This new rowset might include new rows
	added to the table that happen to match the where clause, but it's hard to know
	where the new rows will actually show up (maybe at the end).
	
	RDO only goes back to the server when it needs another rowset of data (again,
	number of rows in a rowset is determined by the RowsetSize property), so changes
	by other users won't show up until the rowset boundary is crossed. Adjusting the
	RowsetSize property is done to balance performance against freshness of data.
	Because frequent trips to the server are very expensive, it is not advisable, in
	a client/server environment where a network is involved, to ping back to the
	server every time you move to a new row - the Jet database engine does this and
	it is not as fast as RDO across the network.
	
	Bookmarks are not supported in Dynamic cursors - the Bookmarkable property will
	always be false for a dynamic cursor. The SQL Server driver doesn't give
	bookmarks in dynamic cursors because there is no immutable row id in SQL Server.
	Bookmarks work within rowsets but not across them, so the Bookmarkable property
	is set to false.
	
	SQL Server cannot be implemented like an ISAM database. The design goal is to
	make a client/server system scalable. RDO allows you to refresh data constantly
	by setting the RowsetSize = 1, but this results in network round- trips (by
	definition) every time you move, and hinder you on a slower network or when many
	users are on the system. This is not an efficient way to implement client/server
	programming, and no DBMS or development tool can address the fact that network
	round-trip's takes time. RDO uses ODBC without introducing any magic on top,
	which is why it is both fast and small.
	
	Sample Program
	--------------
	
	This example describes how to set up a dynamic rdoResultset. It uses a DSN-less
	ODBC connection so it is not necessary to set up a DSN with the ODBC Admin
	utility.
	
	1. Start a new project in Visual Basic. Form1 is created by default. Add a
	  CommandButton to Form1.
	
	2. Paste the following code into the General Declarations section of Form1.
	
	        Private Sub Command1_Click()
	          Dim en As rdoEnvironment
	          Dim cn As rdoConnection
	          Dim rs As rdoResultset
	          Dim sql As String
	
	          'establish connection
	          Set en = rdoEngine.rdoEnvironments(0)
	          en.CursorDriver = rdUseIfNeeded
	          'this should be modified to connect to your database
	          Dim cnStr As String
	
	          cnStr = "driver={SQL Server};server=myserver;" & _
	            "database=pubs;uid=myuid;pwd=mypwd"
	          Set cn = en.OpenConnection(dsName:="", Prompt:=rdDriverNoPrompt, _
	            ReadOnly:=False, Connect:=cnStr)
	
	          'create an SQL statement that matches a table in your database
	          sql = "Select * From Titles"
	          'the next line opens a Dynamic resultset
	          Set rs = cn.OpenResultset(Name:=sql, Type:=rdOpenDynamic, _
	            LockType:=rdConcurRowver, Option:=rdAsyncEnable)
	          While rs.StillExecuting
	            DoEvents
	          Wend
	          'prints first 3 columns of the first row
	          Me.Print rs(0), rs(1), rs(2)
	        End Sub
	
	3. Change your DRIVER, SERVER, DATABASE, UID, and PWD in the OpenConnection
	  method. Modify the SQL statement contained in the Command1_Click event to
	  match your SQL data source.
	
	4. Start the program or press the F5 key. Click on the Command1 button to start
	  the query, which will display the first 3 columns of the first row on the
	  form.
	
	REFERENCES
	==========
	
	For more information on this topic, please see the following:
	
	ODBC 2.0 Programmer's Reference and SDK Guide
	
	Building Client/Server Applications with Visual Basic
	
	Hitchhiker's Guide to Visual Basic and SQL Server, Microsoft Press.
	ISBN: 1-55615-906-4.
	
	Additional query words: kbVBp400 kbVBp600 kbdse kbDSupport kbVBp kbVBp500 kbrdo
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Issue type        : kbhowto kbinfo
	
	=============================================================================
	

{% endraw %}
