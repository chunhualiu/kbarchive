---
layout: page
title: "Q296583: FP98: FrontPage Server Extensions Do Not Work As Expected"
permalink: /kb/296/Q296583/
---

## Q296583: FP98: FrontPage Server Extensions Do Not Work As Expected

{% raw %}

	Article: Q296583
	Product(s): Word Front Page
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 98 for Windows, used with:
	   - the operating system: Microsoft Windows NT 4.0 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 2000 version of this article, see Q296596.
	
	SYMPTOMS
	========
	
	After you install Microsoft FrontPage Server Extensions on a Web, some or all of
	the following symptoms occur:
	
	- In Microsoft FrontPage, you are unable to list Webs from the Web server.
	
	- When you attempt to browse the Web, you receive intermittent error messages
	  similar to the following:
	
	  HTTP Error 405
	  405 Method Not Allowed.
	  The method specified in the Request Line is not allowed for the
	  resource identified by the request. Please ensure that you have the
	  proper MIME type set up for the resource you are requesting.
	
	  Please contact the server's administrator if this problem persists.
	
	- When you view the Event log on the Web server, you notice "Access violation"
	  events with an Event ID of 80002.
	
	
	CAUSE
	=====
	
	Some or all of these issues may occur when you install FrontPage Server
	Extensions on a Web whose root directory is "nested" within the content
	directory of another Web (nested content).
	
	FrontPage Server Extensions (FPSE) installed on a site attempt to control all
	content in that site. When the directory structure of one FPSE-based Web is
	inside that of another, permission conflicts may arise as more than one
	installation of FPSE is applied to the nested Web site.
	
	Each FPSE-based Web site that has been assigned a unique IP address must have its
	content directory at the same level as other uniquely assigned Web sites.
	
	RESOLUTION
	==========
	
	To resolve this issue, move all Web content folders to the same level in the
	directory tree. To do this, follow these steps:
	
	1. Log on to the Web server as administrator.
	
	2. Start FrontPage Server Administrator.
	
	3. Under "Select server or port", click a server or port, click Uninstall, click
	  OK to confirm the removal of the FPSE software from the selected server or
	  port, and then click OK again.
	
	4. Repeat step 3 for every server or port in the "Select server or port" list.
	
	5. Click Close to quit FrontPage Server Administrator.
	
	6. Start Internet Service Manager.
	
	7. Under Console Root, expand Internet Information Server, and then expand
	  *<servername>, where <servername> is the name of the Web server.
	
	8. Right-click a Web site (for example, Default Web Site), and then click Stop
	  on the shortcut menu that appears.
	
	9. Repeat step 8 for each Web site.
	
	10. Click Start, point to Settings, and then click Control Panel.
	
	11. In Control Panel, double-click Services.
	
	12. In the Service dialog box, click "World Wide Web Publishing Service" in the
	  Service list, click Stop, and then click Yes to confirm.
	
	13. Click Close, and then quit Control Panel.
	
	14. Start Windows Explorer, and then navigate to the location of your Web
	  content, for example, C:\InetPub\wwwroot.
	
	  NOTE: Verify that you have a folder between the folders that contain Web
	  content and the rest of the hard disk. This folder acts as a buffer between
	  the Web content and the root of the hard disk.
	
	  Not having this "buffer" folder may result in permissions or security
	  problems with your Web site. In the following directory configuration, the
	  InetPub folder acts as the buffer between Web content stored in wwwroot and
	  the hard disk C.
	
	  C:\InetPub\wwwroot
	
	15. In Windows Explorer, move all nested Web content folders to the buffer
	  folder. All folders containing Web content should now be at the same
	  hierarchy in the directory tree. For example, using the following directory
	  structure
	
	  C:             
	|-InetPub
	   |
	   |- wwwroot         contains Web site A 
	       |
	       |- Folder1     contains Web site B     
	       |
	       |- Folder2     contains Web site C
	
	  move Folder1 and Folder2 to the InetPub folder.
	
	  NOTE: If you have many nested folders and only one "nesting" Web site folder,
	  it may be easier to move the higher-level folder further downward in the
	  directory tree. For example, using the same example directory structure,
	  create a new folder (named Folder), and then move the "Web site A" content
	  from wwwroot into the newly created folder. The new folder listing would
	  appear similar to the following:
	
	  C:             
	|-InetPub
	   |
	   |- wwwroot     
	       |
	       |- Folder      contains Web site A
	       |
	       |- Folder1     contains Web site B     
	       |
	       |- Folder2     contains Web site C
	
	16. In Internet Service Manager, right-click the Web site whose content you
	  moved in step 15 and then click Properties on the shortcut menu that
	  appears.
	
	17. On the Home Directory tab, in the Local Path box, type the new local path to
	  the Web content. For example, "C:\InetPub\Folder1" (without the quotation
	  marks). Click Apply, and then click OK.
	
	18. Repeat steps 16 through 17 for every Web site whose content folder you
	  moved.
	
	19. Restart the "World Wide Web Publishing" service:
	
	  a. Click Start, point to Settings, and then click Control Panel.
	
	  b. In Control Panel, double-click Services.
	
	  c. In the Service dialog box, click "World Wide Web Publishing Service" in
	     the Service list, and then click Start.
	
	  d. Click Close, and then quit Control Panel.
	
	20. Restart the virtual servers that you stopped in step 8. To do this, in
	  Internet Service Manager, right-click the Web site that you want and then on
	  the shortcut menu that appears, click Start.
	
	21. Start FrontPage Server Administrator.
	
	22. In the FrontPage Server Administrator dialog box, click Install.
	
	23. In the Configure Server Type dialog box, click "Microsoft Internet
	  Information Server" in the "Server type" list, and then click OK.
	
	24. In the Multihosted Servers dialog box, select the virtual servers that you
	  want, and then click OK.
	
	25. In the Confirmation Dialog, click OK.
	
	26. In the Administrator Setup for <Web Site Name> dialog box, (where
	  <Web Site Name> is the name of the Web site that you selected, in the
	  Name box, type the account name that you want (for example, "Administrator"
	  (without the quotation marks)), and then click OK.
	
	27. Repeat steps 25 through 26 for each Web site on which the FrontPage Server
	  Extensions are to be installed.
	
	28. On the "Install completed successfully" message that appears after FrontPage
	  Server Extensions are installed on all of the virtual servers that you
	  selected, click OK.
	
	29. Click Close to quit FrontPage Server Administrator.
	
	MORE INFORMATION
	================
	
	Nested content occurs when the root directory of one virtual site is located
	inside (nested in) the content directory of another virtual site.
	
	FrontPage Server Extensions (FPSE) installed on a site attempt to control all
	content in that site. When the directory structure of one FPSE-based Web is
	inside that of another, permission conflicts may arise as more than one
	installation of FPSE is effectively installed on that nested Web site.
	
	Each FPSE-based Web site that has been assigned a unique IP address must have its
	content directory at the same hierarchical level as other uniquely assigned Web
	sites.
	
	Consider the following directory structure.
	
	C:             
	|-InetPub
	   |
	   |- wwwroot         contains Web site A   
	       |
	       |- Folder1     contains Web site B    
	       |
	       |- Folder2     contains Web site C
	
	If you create a Web in Folder1, the content of that Web will be "nested" within a
	Web that you create in wwwroot.
	
	If, in the above example, you install FrontPage Server Extensions on a Web
	created in wwwroot, they will attempt control all content within wwwroot
	including Webs created in Folder1 and Folder2. This may create conflicting
	permissions with FrontPage Server Extensions installed on Webs whose content is
	stored in these folders.
	
	The following example directory structure is better suited to multiple Web sites
	with unique IP addresses:
	
	C:             
	|-InetPub
	   |
	   |- wwwroot     contains Web site A   
	   |
	   |- Folder1     contains Web site B    
	   |
	   |- Folder2     contains Web site C
	
	In this example, when you create a FPSE-based Web in wwwroot, the server
	extensions will not conflict with other FPSE-based Webs created in Folder1 or
	Folder2.
	
	For additional information about troubleshooting FrontPage Server Extensions
	permission issues, click the article numbers below to view the articles in the
	Microsoft Knowledge Base:
	
	  Q198431 Users Cannot Author, Permissions Are Set Correctly in FrontPage
	
	  Q183777 FP: Server Extensions Do Not Support Nested Virtual Roots
	
	  Q173307 PRB: Nested Virtual Roots Can Lose Session State
	
	
	  Q224985 FP98: How to Reset Permissions on Multiple Virtual Servers with
	  FrontPage 98 Server Extensions
	
	  Q224147 How to Reset Permissions Using FrontPage 98 Server Extensions
	
	  Q162144 FP97: Minimum NTFS File Permission Requirements
	
	  Q194475 FP98: Server Extensions Do Not Support Nested Virtual Roots
	
	Additional query words: front page
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch _IKkbZNotKeyword4 kbFrontPage98Search kbZNotKeyword3
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
