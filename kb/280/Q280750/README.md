---
layout: page
title: "Q280750: How to Restore Netscape Communicator as the Default Browser"
permalink: /kb/280/Q280750/
---

## Q280750: How to Restore Netscape Communicator as the Default Browser

{% raw %}

	Article: Q280750
	Product(s): Microsoft Home Miscellaneous Products
	Version(s): 
	Operating System(s): 
	Keyword(s): kb3rdparty kbimu
	Last Modified: 05-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Greetings 2001 
	- Microsoft Picture It! Express 2001 
	- Microsoft Picture It! Photo 2001 
	- Microsoft Picture It! Photo Premium 2001 
	- Microsoft Picture It! Publishing 2001 
	- Microsoft Picture It! Publishing 2001 Gold 
	- Microsoft Picture It! Publishing 2001 Platinum 
	- Microsoft Picture It! Publishing 2001 Silver 
	- Microsoft Works Suite 2000 
	- Microsoft Works Suite 2001 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When you install any of the programs listed at the beginning of this article,
	Microsoft Internet Explorer is installed as your default browser.
	
	This article describes how to restore Netscape Communicator as your default
	browser.
	
	MORE INFORMATION
	================
	
	To restore Netscape Communicator as your default browser, contact Netscape or
	visit the following Netscape Web site:
	
	  http://home.netscape.com/download/win32_instructions.html
	
	To disable Internet Explorer as your default browser:
	
	1. Start Internet Explorer.
	
	2. Click Tools, and then click Internet Options.
	
	3. Click the Programs tab.
	
	4. Click to clear the "Internet Explorer should check to see whether it is the
	  default browser" box.
	
	5. Click OK, and then quit Internet Explorer.
	
	To configure Netscape Communicator to be the default browser:
	
	1. Start Netscape Communicator.
	
	2. If you are prompted with the following message, click Yes:
	
	  "Navigator is no longer registered to handle Internet Shortcuts. Would you
	  like to register Navigator as your default browser?"
	
	  If you are not prompted with a message, follow these steps:
	
	  a. Quit Netscape Communicator.
	
	  b. Click Start, point to Find, and then click "Files or Folders".
	
	  c. In the Named box, type "prefs.js" (without the quotation marks).
	
	  d. In the "Look in" box, click My Computer.
	
	  e. Click Find Now.
	
	  f. In the list of found files, right-click the Prefs.js file, and then click
	     Open.
	
	NOTE: If you are prompted to select a program with which to open the Prefs.js
	file, click Notepad, click to clear the "Always use this program to open these
	files" check box, and then click OK.
	
	  g. In the Prefs.js file, change the following line from
	
	  user_pref("browser.wfe.ignore_def_check", true);
	
	to:
	
	  user_pref("browser.wfe.ignore_def_check", false);
	
	  h. On the File menu, click Save.
	
	  i. On the File menu, click Exit.
	
	  j. Start Netscape Communicator, and then click Yes when you are prompted with
	     the following message:
	
	  "Navigator is no longer registered to handle Internet Shortcuts. Would you
	  like to register Navigator as your default browser?"
	
	Microsoft provides third-party contact information to help you find technical
	support. This contact information may change without notice. Microsoft does not
	guarantee the accuracy of this third-party contact information.
	
	The third-party products that are discussed in this article are manufactured by
	companies that are independent of Microsoft. Microsoft makes no warranty,
	implied or otherwise, regarding the performance or reliability of these
	products.
	
	Additional query words: pip2001
	
	======================================================================
	Keywords          : kb3rdparty kbimu 
	Technology        : kbHomeProdSearch kbWorksSearch kbPictureItSearch kbWorks2000 kbZNotKeyword3 kbPictureItPhoto2001
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
