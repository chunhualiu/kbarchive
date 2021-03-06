---
layout: page
title: "Q141342: XADM: Public Folders Automatically Get New Home Site/Server"
permalink: /kb/141/Q141342/
---

## Q141342: XADM: Public Folders Automatically Get New Home Site/Server

{% raw %}

	Article: Q141342
	Product(s): Microsoft Exchange
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbenv kbtool
	Last Modified: 18-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you look at the properties of a public folder using the Microsoft Exchange
	Server, version 4.0, Administrator program, the Home Site and Home Server
	information may have been changed without any user intervention. The permissions
	on the public folder may also have been changed.
	
	CAUSE
	=====
	
	If there is a public folder in the public information store on a server in one
	site (site1) AND there are no public information stores containing that folder
	in the folder's present home site (site2), then when the DS/IS checker is run on
	a server in site1, it will re-home the folder in its site (to a server that
	contains a public information store).
	
	The state in which a public folder has no replicas in the site where it was
	created could be caused by any of the following situations:
	
	- With the Microsoft Exchange Administrator program, you explicitly remove all
	  servers in the folder's home site from the replica list. The Administrator
	  program will usually not let you remove the last server in the folder's home
	  site from the replica list and will try to prevent this, but it can still be
	  done as follows. Suppose Serv1 and Serv2 are servers in the public folder's
	  home site and contain replicas of the folder. Run the Microsoft Exchange
	  Administrator program against both Serv1 and Serv2. At nearly the same time,
	  in Serv1 remove Serv1 as a replica and in Serv2 remove Serv2 as a replica. On
	  both servers there is one other server in the home site still left in the
	  replica list, but when replication happens, both servers do get removed and
	  the folder can thus be orphaned.
	
	
	- Let Fold1 be a public folder whose replica is only on server, Serv1 in Site1.
	  Let Serv2 be a server in Site2, with Site2 having public folder affinity to
	  Site1. Let a user on Serv2 open folder Fold1. Because of affinity, the user
	  connects to Serv1 and opens the folder. Now, let the user create a subfolder
	  Fold2. The subfolder is physically created in the user's home server Serv2,
	  and initially Serv1 and Serv2 are both in the replica list for Fold2. But,
	  Serv2 is only temporarily in this replica state and will soon be removed by
	  the mdb automatically, leaving only Serv1 as the replica for the subfolder
	  Fold2. This leads to the state of the folder Fold2, being homed in Site2 but
	  having replicas only in Site1. This behavior was needed to support the exact
	  inheritance of replica list when creating a subfolder.
	
	- Create a Fold1 folder on Serv1 present in Site1. Make servers Serv1 and Serv2
	  in sites Site1 and Site2 respectively as replicas. Now delete the connector
	  between the two sites (a site tear down). After this, Serv2 no longer knows
	  about Serv1. Now when the DS/IS checker is run on Serv2, it will create a new
	  DS object for the folder and it will become the home mdb for the folder.
	  After this, reconnect the sites. Initially, the Distinguished Name (DN) of
	  the folder is different in Serv1 and Serv2 (both think they are the home mdb
	  for this folder). After replication occurs, one version will win. If the
	  folder was last changed in Serv2, its version will win and so it will remain
	  the home mdb. So, magically the home mdb is changed from Serv1 to Serv2.
	
	
	Additional query words: exsrv public fld rehome
	
	======================================================================
	Keywords          : kbenv kbtool 
	Technology        : kbExchangeSearch kbExchange400 kbZNotKeyword2
	Version           : :4.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
