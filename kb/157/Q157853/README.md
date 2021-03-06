---
layout: page
title: "Q157853: FIX: Upsizing Wizard Generated SQL Code Causes Errors"
permalink: /kb/157/Q157853/
---

## Q157853: FIX: Upsizing Wizard Generated SQL Code Causes Errors

{% raw %}

	Article: Q157853
	Product(s): Microsoft FoxPro
	Version(s): 5.0 5.0a
	Operating System(s): 
	Keyword(s): kbtool kbvfp kbvfp500aBUG kbvfp500bugkbbuglist
	Last Modified: 23-MAR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When running the SQL code that is generated from either the Oracle or SQL Server
	Upsizing Wizards, an error occurs.
	
	CAUSE
	=====
	
	Some of the comment blocks in the generated SQL code are marked incorrectly.
	
	NOTE: Other errors may occur that are unrelated to this problem.
	
	WORKAROUND
	==========
	
	In the SQL language, a multi-line comment is opened with "/*" and closed with
	"*/". Some of the comment blocks in the generated SQL code are opened with "*/".
	To avoid these errors, change the open comment designators to "/*".
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. This has been corrected in Visual FoxPro 6.0.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Open the Testdata database located in the \Vfp\Samples\Data directory.
	
	2. Start the SQL Server Upsizing Wizard.
	
	3. Click the Next button.
	
	4. Specify a valid SQL Server datasource.
	
	5. Select the customer table from the list of available tables.
	
	6. Click the Finish button.
	
	7. Click "Save generated SQL." Then click the Finish button.
	
	8. Drill-down through the data tree until you've located the sql_uw table.
	
	9. Browse the sql_uw table, and look at the code in the scriptsql memo field.
	
	NOTE: the comment section for "Index code" is opened with "*/".
	
	Additional query words: kbvfp600fix
	
	======================================================================
	Keywords          : kbtool kbvfp kbvfp500aBUG kbvfp500bug kbbuglist
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP500a
	Version           : 5.0 5.0a
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
