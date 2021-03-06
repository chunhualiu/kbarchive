---
layout: page
title: "Q163313: DCA ISCA SDLC Link Service Sets Incorrect Registry Entries"
permalink: /kb/163/Q163313/
---

## Q163313: DCA ISCA SDLC Link Service Sets Incorrect Registry Entries

{% raw %}

	Article: Q163313
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 3.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The symptoms will vary depending on whether this is the first link service
	installed. If this is the first link service installed, most of the registry
	values will be left empty. Most notably, the DependOnService value for SNAServr
	will be missing DCASDLC1, which will cause the SNA Server service to start
	without starting the link service. The server will go to an Active state in SNA
	Manager, but the connection will not change from Inactive. If a previous link
	service is installed, the values will be entered, but incorrectly. In this case,
	the connection will go to a Pending state, but will not establish a connection
	with the host.
	
	CAUSE
	=====
	
	This was caused by an error in the setup file for this link service.
	
	RESOLUTION
	==========
	
	A fix has been made to the setup file for this link service.
	
	The current workaround is to use the DCA SDLC link service from SNA Server 2.11
	Service Pack 1. To do this, use the following steps:
	
	1. In SNA Manager remove the DCASDLC link service.
	
	2. Copy files from the 2.11 SP1 compact disc to the SNA 3.0 installation folder.
	  Copy these files from the <CD>\I386\System\Hwsetup folder of the
	  compact disc to the <Snaroot>\System\Hwsetup folder on the hard disk:
	
	  Dcasdlc.hlp
	  Dcasdlc.srl
	  Dcasdlc.inf
	
	3. Create a folder named Dcasdlc in the \<Snaroot>\System\Hwsetup folder
	  of the hard disk and then copy Dcasync.sys from the
	  \<CD>\I386\System\Hwsetup\Dcasdlc folder to the
	  \<Snaroot>\System\Hwsetup\Dcasdlc folder:
	
	4. Run the External Link Service tools from the Tools menu in SNA Manager.
	
	5. Click Add and select "DCA SDLC link service."
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server for Windows NT. This
	problem was corrected in the latest SNA Server for Windows NT 3.0 U.S. Service
	Packs. For information on obtaining the Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	Additional query words: attachmate sna3sp1
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300
	Version           : WINDOWS:3.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
