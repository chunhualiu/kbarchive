---
layout: page
title: "Q254675: FIX: DTC/MTS Errors Cause Ora-00000 Normal Successful Completion"
permalink: /kb/254/Q254675/
---

## Q254675: FIX: DTC/MTS Errors Cause Ora-00000 Normal Successful Completion

	Article: Q254675
	Product(s): Open Database Connectivity (ODBC)
	Version(s): Build 2.573.2927,Build 2.573.3513,Build 2.573.3711,Build 2.573.4202,Build 2.573.4403
	Operating System(s): 
	Keyword(s): kbDatabase kbDriver kbMDAC kbODBC kbOracle kbDSupport kbMDAC210SP2fix
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft ODBC for Oracle version 2.5, versions Build 2.573.2927, Build 2.573.3513, Build 2.573.3711, Build 2.573.4202, Build 2.573.4403 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When a Microsoft Transaction Server (MTS) or Microsoft Distributed Transaction
	Server (MS DTC) application encounters errors that are MTS-related or MS
	DTC-related, only the following error message is returned to the application:
	
	  DIAG [NA000] [Microsoft][ODBC driver for Oracle][Oracle]ORA-00000: normal,
	  successful completion (0)
	
	This error message is misleading in an environment that uses MTS and MS DTC
	because it masks the location of the true error and prevents useful error
	messages from being returned to the application.
	
	CAUSE
	=====
	
	With the current releases of the Oracle ODBC driver (MSORCL32.DLL) and the
	MTS/OCI layer (Mtxoci.dll), error messages that are generated by the underlying
	MS DTC/MTS layer are not correctly trapped by the Oracle ODBC driver.
	
	The driver incorrectly assumes that the Mtxoci.dll file is reporting only Oracle
	errors, and the driver checks the Errors collection for the Oracle connection to
	retrieve error information. Because there are no Oracle errors, the only error
	message to return is the "normal, successful completion" error message.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Microsoft Data Access Components service pack that contains this
	fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Date      Version        Size             File name     
	  --------------------------------------------------------
	  02/14/00  02.573.5014    138,512 bytes    Msorcl32.dll
	  03/04/00  1999.6.904     87,312 bytes     Mtxoci.dll
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	
	Steps to Reproduce the Behavior
	-------------------------------
	
	1. Configure the Oracle database server to accept only a limited number of
	  client connections, such as 15 or 20. This can be done by modifying the
	  Processes parameter in the Init"sid" (without the quotation marks).ora file.
	  Then, stop and restart the Oracle service.
	
	2. Use Visual Basic to create an ActiveX DLL with one method. Within this
	  method, create an ADO connection to an Oracle database by using the Microsoft
	  ODBC for Oracle driver, create a simple recordset that selects a few records
	  from any table, and then close the recordset and the connection.
	
	3. Compile this DLL and register it under MTS. Mark the DLL as "Requires a New
	  Transaction."
	
	4. Create a client application that creates an instance of the new object, and
	  calls the single method in a loop of about 10 times.
	
	5. Compile this client application to an .exe, and then launch approximately 10
	  instances of it.
	
	6. Notice that some instances of the client application encounter errors when
	  attempting to connect to the Oracle server. Several of the returned errors
	  are the Ora-00000 "Normal, successful completion" errors.
	
	Additional query words: ora-00000 normal successful completion oracle error mts transaction distributed server
	
	======================================================================
	Keywords          : kbDatabase kbDriver kbMDAC kbODBC kbOracle kbDSupport kbMDAC210SP2fix 
	Technology        : kbAudDeveloper kbODBCSearch kbODBCOracle25732927 kbODBCOracle25733513 kbODBCOracle25733711 kbODBCOracle25734202 kbODBCOracle25734403 kbODBCOracle250Search
	Version           : :Build 2.573.2927,Build 2.573.3513,Build 2.573.3711,Build 2.573.4202,Build 2.573.4403
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	