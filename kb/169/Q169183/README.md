---
layout: page
title: "Q169183: XCLN: Unable to Get Published Folder List"
permalink: /kb/169/Q169183/
---

## Q169183: XCLN: Unable to Get Published Folder List

{% raw %}

	Article: Q169183
	Product(s): Microsoft Exchange
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Windows 3.x client, version 5.0 
	- Microsoft Exchange Windows 95/98 client, version 5.0 
	- Microsoft Exchange Windows NT client, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to read the contents of a public folder from a Web Browser with
	anonymous access via the Microsoft Exchange Active Server Components, the
	following error may occur:
	
	  Unable to get published folder list.
	
	This error can occur if anonymous folder access is not configured correctly.
	
	RESOLUTION
	==========
	
	Verify that the following are true.
	
	1. Verify that the IIS server's WWW service is running and handling ASP
	  requests. This can be done by running some of the sample scripts available
	  with IIS.
	
	  NOTE: Anonymous access from the WWW service properties is not required for
	  anonymous access to Microsoft Exchange Public Folders.
	
	2. From the Microsoft Exchange Administrator program, confirm that the HTTP
	  protocol is enabled and allows for anonymous access to public folders. you
	  can do this by expanding the Site container, configuration container,
	  protocols container, opening the HTTP protocol properties page, and clicking
	  on the General tab.
	
	3. From the HTTP protocol properties page, select the Folder Shortcuts tab.
	  Verify that the folder(s) for anonymous access are available in the Public
	  Folder Shortcuts listbox.
	
	  NOTE: Including only the Public Folder folder tree object will not provide
	  anonymous access to any of the top level Public Folders.
	
	4. Verify that the folder has access permissions. On the Public Folder Shortcuts
	  tab, click the Client Permissions button. Make sure that the default
	  permissions for the anonymous account are set to a minimum of Reviewer.
	
	5. Verify that the Public Folder(s) you are trying to open is available from the
	  Microsoft Exchange client (most likely, from a LAN or WAN connection). This
	  should ensure that the public folder is accessible.
	
	6. If you are still having problems, setup a test folder and add it to the list
	  of folders and assign the appropriate permissions. Remember to exit the
	  Browser and restart it before attempting to access the test public folder.
	
	7. Make sure that the IUSR_SERVER account (whether PDC, BDC, or Member Server)
	  has log on locally rights on the IIS Server.
	
	8. Make sure that the IUSR_SERVER account's password in the Windows NT User
	  Manager is the same as in the Internet Service Manager.
	
	  NOTE: When accessing the active server components for anonymous access, the
	  user should be presented with the Microsoft Exchange Logon ASP page
	  (Logon.asp).
	
	======================================================================
	Keywords          :  
	Technology        : kbExchangeSearch kbExchange500 kbExchangeClientSearch kbZNotKeyword kbZNotKeyword2 kbZNotKeyword3 kbExchange500NT kbExchange500Win95
	Version           : 5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
