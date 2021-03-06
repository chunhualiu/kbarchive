---
layout: page
title: "Q205862: XFOR: Installing Address Generators for Notes, SNADS, OV/VM"
permalink: /kb/205/Q205862/
---

## Q205862: XFOR: Installing Address Generators for Notes, SNADS, OV/VM

{% raw %}

	Article: Q205862
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55
	Last Modified: 25-JUN-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Exchange Server 5.5 includes additional connectors that connect Exchange Server
	to Lotus Notes, SNADS, and IBM OfficeVision/VM (PROFS or OfficeVision). These
	connectors are based on the Microsoft Exchange Server Development Kit
	specifications for gateways that are comprised of connector and e-mail address
	generating components. You only need to install the connectors on Exchange
	Server systems that connect to foreign e-mail systems. Install the connectors on
	at least one server in the organization.
	
	You need to install the e-mail address generators for the connectors on at least
	one server in every site. The address generators interchange e-mail with the
	foreign systems that are accessible through the connectors that are installed
	throughout the organization. This article provides instructions to install only
	the address generator for the connectors.
	
	MORE INFORMATION
	================
	
	To install only the e-mail addressing components for Lotus Notes, SNADS, and IBM
	OfficeVision/VM:
	
	1. On the Exchange Server 5.5 installation CD-ROM, open the
	  Server\Exchconn\Setup folder.
	
	2. From this folder, start the Setup.exe program. The Welcome dialog box is
	  displayed. Click Next. The Select Installation Option dialog box is
	  displayed.
	
	3. Click Microsoft Exchange Connectivity Service, and then click Next. The
	  Software Selection dialog box is displayed, in which you can select the
	  address components that you want to install.
	
	4. Click to select the check boxes for any combination of the Lotus Notes,
	  SNADS, and IBM OfficeVision/VM addressing components to install the
	  components.
	
	  NOTE: If you do not want to install connectors, do not click to select the
	  check boxes for the connectors.
	
	At this point, the wizard installs the components that you selected in the
	preceding steps. Additional configuration information is requested for each
	component. The Lotus Notes addressing component requires the Lotus Notes domain
	name to use as the Exchange Server organization or site. The SNADS component
	requires the Distribution Group Name (DGN) ID to use as the Exchange Server
	organization. The IBM OfficeVision/VM component requires the Node ID to use as
	the organization.
	
	To verify that the addressing component is installed, open the Exchange Server
	Administrator program and select a server in the site. Open the Site Address
	properties and make sure that the components that you selected in the preceding
	steps are listed. You can open the Site Address properties by clicking the
	Configuration object for the site, and then double-clicking the Site Addressing
	object that is displayed in the right pane.
	
	NOTE: You can also install these components by using the latest Web releases or
	service pack releases of the connectors and the Microsoft Exchange Connector for
	Novell GroupWise. The steps to install an addressing component by using the
	latest Web releases or service pack releases are similar, but there may be
	slight differences. Refer to the documentation that is included in the Web
	release or service pack release for additional information.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
