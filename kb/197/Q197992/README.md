---
layout: page
title: "Q197992: How to Configure WLBS Using a Single Network Interface Card"
permalink: /kb/197/Q197992/
---

## Q197992: How to Configure WLBS Using a Single Network Interface Card

{% raw %}

	Article: Q197992
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition 
	- Microsoft Windows NT Load Balancing Service 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When installing Windows NT Load Balancing Service (WLBS) in a system with a
	single network interface card (NIC), make sure that you have read the following
	Microsoft Knowledge Base article:
	
	  Q197999 Single Network Interface Card Limitations with WLBS
	
	Multicast support is enabled by default. However, if you disable multicast
	support, this hardware configuration is not preferred because it limits
	networking performance and functionality. However, WLBS always can be
	successfully configured with one NIC.
	
	MORE INFORMATION
	================
	
	To set the WLBS bindings for use with one network interface card, follow these
	steps:
	
	1. In Control Panel, double-click Network and then click the Bindings tab.
	
	2. In the Show Binding For drop down list, select All Protocols.
	
	  The bindings for all installed networking protocols can be displayed and
	  modified in this dialog box. Note that WLBS Driver appears in the list of
	  protocols. For each protocol, you can see the network interface cards (NICs),
	  also known as adapters, to which each protocol is bound.
	
	3. Click the plus sign (+) to the left of each protocol to see the adapters to
	  which it is bound. When the bindings are displayed, you will see a minus sign
	  (-) to the left of the protocol.
	
	  You will note that WLBS Virtual NIC appears in the list of adapters for the
	  TCP/IP and WINS Client protocols. WLBS registers itself with Windows NT as
	  both a protocol and as a virtual network adapter. In addition, you should see
	  only one hardware adapter corresponding to the actual NIC installed in your
	  system. If you see more than one hardware adapter, please consult the "Using
	  Multiple Network Interface Cards" help topic.
	
	To set the proper bindings, follow these steps:
	
	1. Enable the binding from the WLBS Driver to the WLBS Virtual NIC adapter. To
	  enable a binding, select the adapter and click Enable.
	
	2. Enable the binding from the WLBS Driver to the network adapter.
	
	3. Enable the binding from the TCP/IP Protocol to the WLBS Virtual NIC adapter.
	
	4. Disable the binding from the TCP/IP Protocol to the network adapter. To
	  disable a binding, select the adapter and click Disable.
	
	5. Enable the binding from the WINS Client to the WLBS Virtual NIC adapter.
	
	6. Disable the binding from the WINS Client to the network adapter.
	
	  NOTE: Other protocols will not be able to bind to WLBS Virtual NIC and will
	  stay bound to the hardware network adapter.
	
	7. Click Close to initiate the rebinding of network components by Windows NT.
	
	During this process, the new binding configuration will be stored in the Windows
	NT registry, and selected software components will review it. WLBS will check
	the interconnection for validity and may warn you if it discovers a problem.
	
	It is highly recommended that you correct any binding problems right away before
	restarting your computer, or your network may not be accessible when you restart
	it.
	
	During the binding review, the TCP/IP protocol will discover that it is bound to
	a new network adapter, the WLBS Virtual NIC, and it will display the Microsoft
	TCP/IP Properties dialog box. This dialog box is displayed the first time you
	establish the binding so that TCP/IP can set up IP addresses for the adapter.
	You also can call the dialog box later to make changes by selecting TCP/IP in
	the list of protocols on the Protocols tab in the Network utility and then
	clicking Properties.
	
	To set up TCP/IP for WLBS, follow these steps:
	
	1. Select WLBS Virtual NIC from the list of adapters in the drop down list.
	
	2. Enter this host's dedicated IP address in the space for the IP address.
	
	  Because TCP/IP is only bound to the WLBS Virtual NIC, it becomes this host's
	  only TCP/IP interface to the network. It is imperative that the dedicated IP
	  address be entered here so that all outbound connections made on behalf of
	  this host (for example, Telnet or FTP) are initiated with this IP address.
	  You will enter the cluster IP address below.
	
	3. Enter the subnet mask and default gateway information for your TCP/IP
	  network.
	
	4. Click Advanced to call the dialog box that lets you add more IP addresses.
	
	5. Click Add and enter the cluster IP address in the space for the IP address
	  followed by the appropriate subnet mask. This IP address corresponds to the
	  primary cluster IP address that you entered in the WLBS Setup dialog.
	
	  If you need to configure additional IP addresses for your cluster (for
	  example, if you are running a multihomed Web server), you can enter them by
	  clicking Add and entering the appropriate information.
	
	6. When you are done adding cluster IP addresses, click OK to close the Advanced
	  IP Addressing dialog box and return to the Microsoft TCP/IP Properties dialog
	  box.
	
	7. Click the WINS Address tab and fill out the information so that it resembles
	  the setup for the dedicated adapter.
	
	8. Click OK.
	
	This completes the steps required to bind WLBS with your other networking
	components and to setup the necessary TCP/IP parameters when using a single
	network interface card.
	
	Additional query words: Convoy
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTS400search kbWinNTS400 kbWinNTLBSSearch
	Version           : winnt:4.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
