---
layout: page
title: "Q135753: Implications of Using NULL in Data Validation Rules"
permalink: /kb/135/Q135753/
---

## Q135753: Implications of Using NULL in Data Validation Rules

{% raw %}

	Article: Q135753
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Because Data Validations are expressions, NULL values inserted into fields and
	passed to Data Validation expressions behave in a consistent manner with that of
	other expressions. If the Data Validation for a field resolves to True (.T.) or
	False (.F.) with a NULL value, that logical result is accepted. In many cases,
	the expression will evaluate to NULL (For example, NULL > 1000). In this
	case, because the expression returns NULL, not True or False, it is rejected.
	
	MORE INFORMATION
	================
	
	Step-by-Step Example
	--------------------
	
	1. Create a program called Myprog.prg
	
	2. Type in the following code segment:
	
	     CREATE DATABASE mydata1
	     CREATE TABLE mytable (lastname c(20) NULL, firstname c(20) NULL, ;
	        city c(20) NULL CHECK city>"a")
	     INSERT INTO mytable (lastname,firstname,city) ;
	        VALUES ("Ansarti","Jim","San Jose")
	     INSERT INTO mytable (lastname,firstname,city) ;
	        VALUES ("Hayden","Rance",.NULL.)
	     INSERT INTO mytable (lastname,firstname,city) ;
	        VALUES ("Putnam","Phil","New Orleans")
	
	3. Save the program.
	
	4. In the Command window, type:
	
	     DO Myprog.prg
	
	5. The program executes, and the INSERT command with city equal to .NULL.
	  generates the error message, "Field City Validation rule is violated."
	
	Additional query words: 3.00 VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
