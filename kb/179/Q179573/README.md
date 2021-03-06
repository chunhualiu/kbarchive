---
layout: page
title: "Q179573: XADM: Orphaned Objects and Exchange Server Directory"
permalink: /kb/179/Q179573/
---

## Q179573: XADM: Orphaned Objects and Exchange Server Directory

{% raw %}

	Article: Q179573
	Product(s): Microsoft Exchange
	Version(s): winnt:4.0,5.0,5.5
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0, 5.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An object persists in the directory of a remote site even though the object has
	been deleted from its original site.
	
	CAUSE
	=====
	
	Typically, the site that still contains the object failed to receive a replica
	of that object prior to the object's tombstone expiring. Once an object's
	tombstone expires, it is no longer considered an "object," and is not
	replicated. See MORE INFORMATION, below.
	
	RESOLUTION
	==========
	
	There are two possible approaches to resolution: re-creating the orphaned object
	in its "original context" or re-orienting replication bridgehead servers. The
	second method has a slim chance of resolving the issue, but may be worth a try
	if the Tombstones of the deleted objects have only recently expired in the
	feeder site.
	
	Method 1. Re-create the Orphaned Object in Its "Original Context"
	-----------------------------------------------------------------
	
	1. Create the object so that it has its original distinguished name (DN); for
	  instance, an orphaned mailbox should be re-created in the original site and
	  so on, such that its "Obj-Dist-Name" attribute matches that of the orphaned
	  object as viewed in Raw Properties in the Administrator program.
	
	2. Modify some attribute of this re-created object until the "Object Version"
	  attribute value exceeds the "Object Version" value on the orphaned object as
	  viewed in in Raw Properties in the Administrator program.
	
	3. Allow the re-created object to replicate to the site(s) maintaining an
	  orphaned replica.
	
	4. Verify that the new replica has replicated to the orphan's site by viewing
	  the orphan's "Object Version" attribute; it should increase to the value
	  incremented in step 2 above.
	
	5. Delete the re-created object in its origin site. This deletion should now
	  replicate to all sites.
	
	Or...
	
	Method 2. Re-orient Replication Bridgehead Servers
	--------------------------------------------------
	
	This method involves re-orienting replication bridgehead servers between the site
	maintaining the orphan and the site that "feeds" that context to the orphan
	site. This assumes that at least two servers in each site exist, and that the
	servers that are not currently replication BHs can assume this role, at least
	temporarily. This will result in a full refresh of all objects from all contexts
	previously provided by the "feeder" site; thus including the refresh of the
	orphan object context.
	
	NOTE: A third option would be to break the replication connector between the
	orphan site and its "feeder" site. This should only be a last resort, because it
	has a much higher impact on other servers in the site and any downstream sites,
	and certainly should avoided in larger organizations when the orphan site is
	also a "feeder" site to additional downstream sites.
	
	MORE INFORMATION
	================
	
	Object Deletion, Tombstone Lifetime, Tombstone Expiry, and Garbage
	Collection Interval
	--------------------------------------------------------------------------------------
	
	When a directory object (also known as a specific Naming Context or NC) is
	deleted (be it a mailbox, Customer Recipient (CR), Distribution List, Connector,
	and so on, hidden or not), a tombstone property (date and timestamp that the
	delete of the object was performed) is added to the object's properties, an
	"IsDeleted" attribute is added and set to TRUE, and the object is "hidden" from
	view.
	
	These attribute changes should result in the replication of this "new" version of
	the object to ALL other directories. Within each directory, a garbage collection
	thread routinely executes (based on value specified for
	<site>\Configuration\DS Site Configuration\Garbage Collection Interval)
	and removes objects whose "IsDeleted" attribute is TRUE, and whose tombstone
	property is older than:
	
	  the current date\time minus the value specified for
	  <site>\Configuration\DS Site Configuration\Tombstone Lifetime
	
	The defaults for Tombstone Lifetime and Garbage Collection Interval are 30 days
	and 12 hours, respectively. So, by default, any object whose tombstone (date the
	object was deleted in the Administrator program) is older than 30 days (from
	"now") will be garbage collected (which actually means having most properties
	stripped off, leaving only a small stub in the directory).
	
	Orphaned Objects
	----------------
	
	If conditions (configuration, hardware or network problems, and so on) prevent
	one or more other sites (or local site directories) from receiving an update of
	a naming context (NC) during the tombstone period, these other sites (and
	servers) never find out that the objects have been flagged for deletion. Once
	the tombstone expires in the originating site, the object is removed from that
	site's directory, and there is no longer an object to replicate. Since the
	tombstone never replicated to some other servers, and since the only writable
	copy of the object has now been deleted, these objects are orphaned in site(s)
	that never received a replica of the object with the "IsDeleted" flag and
	tombstone "timestamp".
	
	WARNING: Tombstone lifetime and Garbage Collection Interval are site-wide
	attributes. Reducing the Tombstone lifetime within a site to a value of only a
	few days can increase the possible occurrence of orphaned objects - particularly
	in large organizations, where it can be more difficult to assess the state of
	replication organization wide. There is little to gain from reducing this value,
	and it is not recommended. The minimum value is two days.
	
	WARNING: Use of "MTACHECK /RD" to remove directory replication messages from a
	backlogged MTA queue may contribute to orphaned objects. This procedure should
	NOT be used as a routine method of reducing MTA backlogs. The real solution is
	to find the cause of the backlog, and resolve that problem. If it is determined
	that directory replication scheduling has been set to "ALWAYS", and that this
	has resulted in MTA queue backlogs, then "MTACHECK /RD" might be appropriate
	AFTER scheduling has been correctly set.
	
	Determining the Original Context of Orphaned Objects
	----------------------------------------------------
	
	View the object's raw properties. The following attributes can be revealing:
	
	- Obj-Dist-Name: This is the full DN of the object, and specifies the precise
	  location (origin context) of the object in the directory information tree
	  (DIT). This should be all that's needed to identify an orphaned object's
	  origin.
	
	- DSA-Signature: This corresponds to a particular directory's Invocation- ID,
	  and identifies the directory responsible for having this copy of the object
	  written to the current directory. Note that the server originating the orphan
	  may no longer exist in the organization.
	
	  
	
	
	- Hide from AB: This can be tricky, because hidden objects will not be viewable
	  by default. This can exacerbate "mysteriously recurring address book views".
	  A Microsoft Knowledge Base article should be available on this topic soon.
	
	- Object-Version: This is an object-specific, monotonically increasing value
	  for an object - organization wide. If an object has fully replicated
	  throughout the organization, all directories will have the same value in this
	  attribute. If an object is orphaned in numerous places, then determine which
	  of orphans maintains the "highest" Object- Version value. If re- creating the
	  original object (option #1 above) modify the re-created object until its
	  Object-Version exceeds the highest value found among the orphans. This will
	  ensure that the orphan will later be successfully deleted throughout the
	  organization.
	
	- When-Created: Date\timestamp the object was created.
	
	- When-Changed: Date\timestamp of the most recent replica update.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange550 kbExchange400 kbZNotKeyword2
	Version           : winnt:4.0,5.0,5.5
	
	=============================================================================
	

{% endraw %}
