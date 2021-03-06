---
layout: page
title: "Q130200: PRB: Deleted Records are Committed with TABLEUPDATE"
permalink: /kb/130/Q130200/
---

## Q130200: PRB: Deleted Records are Committed with TABLEUPDATE

{% raw %}

	Article: Q130200
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbvfp300 kbvfp500 kbvfp600
	Last Modified: 20-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A table is opened and table buffering is enabled. During execution of a program,
	records are added and deleted. When the TABLEUPDATE(.T.) function is used to
	commit the changes, the records that were appended and then deleted are also
	committed to the table, and they retain their deleted status. You might expect
	that records appended and then deleted would not be included in the table, but
	this is not the case.
	
	CAUSE
	=====
	
	Deleting a record does not actually delete information. The delete flag is
	logical information that determines whether a record needs to be removed at a
	later date. In the same fashion, deleting a record while buffering is enabled
	places a flag in the record, so the record (with the delete flag) is committed
	when a TABLEUPDATE is issued.
	
	RESOLUTION
	==========
	
	If you do not want newly added and deleted records to be committed, you can scan
	the table and search for the appended records. If an appended record has been
	deleted, use the TABLEREVERT() function to discard changes. The following
	example illustrates this alternative. This example uses local data.
	
	     CLOSE ALL
	     CLEAR ALL
	     SET MULTILOCKS ON
	     SET EXCLUSIVE OFF
	     **************************************************
	     * CREATES A SAMPLE DATABASE AND A SAMPLE TABLE
	     ***************************************************
	     CREATE DATA test
	     CREATE TABLE Tblbuffer (field1 I , field2 c(10))
	     INSERT INTO tblbuffer  VALUES (1, 'first')
	     INSERT INTO tblbuffer VALUES (2, 'second')
	     INSERT INTO tblbuffer  VALUES (3, 'third')
	     ****************************************************
	     * Sets Optimistic Table Buffering on
	     ****************************************************
	
	     =CURSORSETPROP('buffering',5)
	     ****************************************************
	     * Appends two blank records and deletes one
	     ****************************************************
	     APPEND BLANK
	     REPLACE field2 WITH 'ABC'
	     APPEND BLANK
	     REPLACE field2 WITH  'DEF'
	     DELETE
	     ******************************************************
	     * Updates table. If records have an append status, check
	     * for their deleted flag. If they are deleted , issue a
	     * TABLEREVERT().
	     *
	     GO TOP
	     liNextRecord=RECNO()
	     DO WHILE liNextRecord!=0
	     IF DELETED() AND "4" $ STR(GETFLDSTATE(0))
	         =TABLEREVERT()
	     ELSE
	         =TABLEUPDATE()
	     ENDIF
	      liCurrRecno=RECNO()
	      liNextRecord=GETNEXTMODIFIED(liCurrRecno)
	      IF !EOF()
	        SKIP
	      ENDIF
	      ENDDO
	
	     ** BROWSE the table to see the problem
	     BROWSE
	
	STATUS
	======
	
	This behavior is by design.
	
	REFERENCES
	==========
	
	For more information about the GETFLDSTATE() function, search for GETFLDSTATE()
	in the Visual FoxPro Help file.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          : kbcode kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP500 kbVFP600
	Version           : WINDOWS:3.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
