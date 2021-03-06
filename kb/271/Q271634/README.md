---
layout: page
title: "Q271634: XADM: How to Apply Exchange Server 5.5 Fixes to Cluster"
permalink: /kb/271/Q271634/
---

## Q271634: XADM: How to Apply Exchange Server 5.5 Fixes to Cluster

{% raw %}

	Article: Q271634
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55
	Last Modified: 30-MAR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If you download a recent recommended fix that is in the SMS Installer format
	from Microsoft, there are special considerations that you need to be aware of
	when you apply the fix to a computer that is running Microsoft Cluster Server.
	
	MORE INFORMATION
	================
	
	An example of a recent recommended fix that is in the SMS Installer format is
	the Q248838engi.exe fix that is described in the following Microsoft Knowledge
	Base article:
	
	  Q248838 XADM: Exchange Server 5.5 Post-SP3 Information Store Fixes Available
	
	You must perform the following steps to apply a fix to a cluster server because
	SMS Installer fixes are not cluster aware:
	
	1. Use Cluster Administrator to manually stop the Exchange Group on the active
	  node.
	
	2. Apply the SMS Installer format fix on the owning node.
	
	3. Move the Exchange Group to the other node.
	
	4. Apply the SMS Installer format fix on the owning node.
	
	5. Move the Exchange Group to the node that you want to run the Exchange Group
	  on.
	
	6. Start the Exchange Group in Cluster Administrator.
	
	Additional query words: Hotfixes Cluster hotfix
	
	======================================================================
	Keywords          : exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
