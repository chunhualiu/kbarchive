---
layout: page
title: "Q187788: BUG: &quot;No Result&quot; Error Saving Oracle Parameterized View"
permalink: /kb/187/Q187788/
---

## Q187788: BUG: &quot;No Result&quot; Error Saving Oracle Parameterized View

{% raw %}

	Article: Q187788
	Product(s): Microsoft FoxPro
	Version(s): 2.5,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbvfp500aBUG kbvfp500bug kbvfp600bug kbDSupport kbMDAC250
	Last Modified: 11-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	- Microsoft Data Access Components version 2.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After creating a parameterized remote view to an Oracle 8.0 table using the
	Oracle 8.0 ODBC driver, the following error occurs when you try to save the
	remote view:
	
	  No result set has been returned by the server.
	
	The remote view runs while in design mode, but saving the remote view causes the
	error to occur. This error does not occur when using the Microsoft Oracle ODBC
	driver.
	
	RESOLUTION
	==========
	
	Use the Microsoft Oracle ODBC driver. Please see the article listed in the
	REFERENCES section for information on obtaining the Microsoft Oracle ODBC
	driver.
	
	STATUS
	======
	
	Microsoft has confirmed this to be an incompatibility with the ODBC driver from
	Oracle and the Microsoft products listed at the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a remote view using an Oracle 8.0 ODBC driver that uses an Oracle
	  table.
	
	2. In the Open dialog box, select a table.
	
	3. Click the Fields tab and select some fields. From the Query, choose "View
	  Parameters".
	
	4. In the View Parameters dialog box, type "xyz" (without the quotes) in the
	  Name text box. In the Type box, type or select a field type to match a field
	  in the table. Press OK to exit the View Parameters dialog box.
	
	5. In the View Designer dialog box, click the Filter tab. In the Field Name box,
	  select a field with the same data type as the variable "xyz" created in step
	  4. Type "?xyz" (without the quotes) in the Example text box.
	
	6. Run the remote view and type something into the View Parameters dialog box.
	  Note that the remote view returns data if it find a matching record.
	
	7. Save the remote view and note that the error occurs. There is no way to save
	  the remote view unless you remove the parameter statement from the View
	  Parameters dialog box.
	
	REFERENCES
	==========
	
	For information on obtaining the Microsoft Oracle ODBC driver, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q175018 HOWTO: Acquire and Install the Microsoft Oracle ODBC Driver
	
	
	Additional query words: FxinteropOdbc FxtoolQueryvwdes
	
	======================================================================
	Keywords          : kbvfp500aBUG kbvfp500bug kbvfp600bug kbDSupport kbMDAC250 
	Technology        : kbVFPsearch kbAudDeveloper kbMDACSearch kbMDAC250 kbVFP500 kbVFP600 kbVFP500a
	Version           : :2.5,5.0,5.0a,6.0
	Issue type        : kbbug
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
