---
layout: page
title: "Q197306: How to Troubleshoot SSL in Internet Information Server 4.0"
permalink: /kb/197/Q197306/
---

## Q197306: How to Troubleshoot SSL in Internet Information Server 4.0

{% raw %}

	Article: Q197306
	Product(s): Internet Information Server
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 01-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to troubleshoot Secure Sockets Layer (SSL)
	functionality in Microsoft Internet Information Server 4.0. It is divided into
	the following sections:
	
	- Key Manager
	
	- Microsoft Management Console (MMC)
	
	- Standard SSL connectivity
	
	- SSL with Client Certificates
	
	MORE INFORMATION
	================
	
	Key Manager
	-----------
	
	Key Manager is an application that allows for the installation of Server
	Certificates for the SMTP and WWW services. The following points are important
	to remember when you use this application:
	
	- After you perform any operations in Key Manager, commit the changes. This can
	  be done through the Computers menu option or when exiting. If Key Manager is
	  closed without saving changes or if the application is left open, then the
	  creation, deletion, or changes made to a key will not be implemented.
	
	- Unless an installed key is associated with an IP Address and Port (this
	  includes "Any Unassigned"), the key will not be available to the appropriate
	  service.
	
	- After a change is committed in Key Manager, it is necessary to restart the
	  Inetinfo process for proper functionality. To do this, Stop the IIS Admin
	  Service in Control Panel Services, and then restart all appropriate
	  subordinate services, such as the World Wide Web Publishing service.
	
	Microsoft Management Console (MMC)
	----------------------------------
	
	The properties for a Web site include the following important configuration
	options:
	
	1. On the Master Properties sheet of Internet Information Server, click the
	  ISAPI Filters tab. There should be a listing for "sspifilt" with the Status
	  showing a green, upward-pointing arrow and a Priority of "HIGH."
	
	2. On the Web site Properties tab, the SSL Port should be set to 443.
	
	3. On the Secure Communications area of the Directory security tab, click to
	  select the "Require secure channel when accessing this resource" check box.
	
	NOTE: If instead of an Edit button being displayed on the Directory Security tab,
	the button displays "Key Manager," the WWW Service is unaware of a key for SSL.
	If a key is installed already in Key Manager, see the "Key Manager" section of
	this document.
	
	Standard SSL Connectivity
	-------------------------
	
	If you follow the "Key Manager" and "Microsoft Management Console" sections
	above, and SSL is not fully functional, see the following:
	
	- If a Web browser displays no error and simply times out, the cause may be one
	  of the following:
	
	   - A router or firewall on the network is blocking TCP port 443.
	
	   - The Sspifilt.dll ISAPI filter is not loaded properly. See step 1 in the
	     Microsoft Management Console section above.
	
	- If you use Internet Explorer 3.02 and the error "A connection with the server
	  could not be established" occurs, the Root Certificate (signer) of your SSL
	  key in not installed in the browser.
	
	- If Microsoft Proxy Server 2.0 is installed on the Internet Information Server
	  computer, Web Publishing must be enabled. In addition, if Packet Filtering is
	  being used, a packet filter for TCP Port 443 must be added.
	
	- Secure Sockets Layer does not function properly when you implement HOST
	  Headers on a Web site.
	
	The HOST header is packaged in the HTTP request, which is in-turn encrypted in
	the TCP packet. The TCP packet is sent to a specific IP address and the HTTP
	request is opened by the first Web site bound to that IP. Because many HOST
	header Web sites may bound to an IP address, unexpected results may occur.
	
	SSL with Client Certificates
	----------------------------
	
	If client authentication is enabled, but not fully functional, see the
	following:
	
	- The Web server returns a 403.7 Client Certificate required message. This
	  message is a generic error from the Web server; it can indicate several
	  conditions:
	
	   - There is no Client Certificate installed in the browser.
	
	   - The Client Certificate supplied is not yet valid or is corrupt.
	
	- An empty Client Certificate dialog appears when you access a client
	  authentication Web site, which may indicate one of the following conditions:
	
	   - There is no Client Certificate installed in the browser.
	
	   - Service Pack 4 is installed. See the following Knowledge Base article for
	     more information:
	
	  Q194788 : Windows NT Service Pack 4 and Client Certificates
	
	NOTE: Due to known issues with the Service Pack 3 version of the Schannel.dll
	file, it is highly recommended that you apply Service Pack 4 to any server
	relying on SSL functionality.
	
	Additional query words: SSL Key Manager Certificate
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis400
	Version           : :4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
