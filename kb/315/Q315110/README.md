---
layout: page
title: "Q315110: Streets and Trips 2001: Cannot Show and Hide Pushpin Sets"
permalink: /kb/315/Q315110/
---

## Q315110: Streets and Trips 2001: Cannot Show and Hide Pushpin Sets

{% raw %}

	Article: Q315110
	Product(s): Microsoft Automap
	Version(s): 
	Operating System(s): 
	Keyword(s): kbimu
	Last Modified: 29-JAN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Streets and Trips 2001 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	In Microsoft Streets and Trips 2001, you cannot select a specific Pushpin set
	from a group of sets, and then display it on the map. You are able to do this in
	Microsoft Streets and Trips 2000.
	
	CAUSE
	=====
	
	This behavior occurs because of a change in the way that Pushpin sets are
	handled in Streets and Trips 2001.
	
	Pushpin sets in Streets and Trips 2000 are saved as .stp files, and they are
	separate from the map file. In Streets and Trips 2001, Pushpin sets are saved to
	the map file. They are components of the map and cannot be separated from it.
	This behavior is by design.
	
	WORKAROUND
	==========
	
	To work around this behavior, use any of the following methods.
	
	Method 1: Create a Different Map for Each Pushpin Set
	-----------------------------------------------------
	
	Create a different map for each set of Pushpins that you want to use. To do this,
	follow these steps:
	
	1. Start Streets and Trips.
	
	2. Click New on the File menu, double-click "New North American Map", and then
	  click OK.
	
	  A new map with the default map view is displayed in the map pane.
	
	3. Create the Pushpins that you want for your new map. To do this, use any of
	  the following methods:
	
	   - Use the Import Data Wizard to import a specific list of addresses from
	     another program such as Microsoft Outlook, Microsoft Excel, or Microsoft
	     Access to your map. To start the Import Data Wizard, click Import Data on
	     the File menu.
	
	     -or-
	
	   - Use the Import Data Wizard to import a Streets and Trips 2000 Pushpin set
	     to your map. To start the Import Data Wizard, click Import Data on the
	     File menu.
	
	     -or-
	
	   - Create the Pushpin set. To do this, follow these steps:
	
	     a. To create a new Pushpin, click Pushpin on the Drawing toolbar.
	
	     b. Click the exact location on the map where you want to place the
	        Pushpin.
	
	     c. In the gray bar of the text balloon, double-click Untitled, and then
	        type a title for your Pushpin.
	
	     d. In the white bar of the text balloon, type the text that you want to
	        add to the Pushpin note (if any).
	
	     e. Click X in the upper-right corner of the text balloon to close it.
	
	     f. Repeat steps a through e to create the Pushpins that you want to
	        display on the map.
	
	The Pushpins that you create are placed in the My Pushpins set by default.
	
	4. Click Save on the File menu.
	
	5. In the Save As dialog box that appears, specify a name and location where you
	  want to save your map, and then click Save.
	
	Method 2: Create a Master Map That Contains All Pushpins
	--------------------------------------------------------
	
	Create one "master" map that contains all of the Pushpins that you want to use,
	and then group the Pushpins into Pushpin sets. When you want to view a specific
	set of Pushpins, open the map, remove the Pushpin sets that you do not want to
	display on this map, and then save the map with a new name. To do this, follow
	these steps:
	
	Create the Master Map:
	
	1. Start Streets & Trips.
	
	2. Create the Pushpins that you want for your master map. To do this, use any of
	  the following methods:
	
	   - Use the Import Data Wizard to import addresses from another program such
	     as Microsoft Outlook, Microsoft Excel, or Microsoft Access to your map. To
	     start the Import Data Wizard, click Import Data on the File menu.
	
	     -or-
	
	   - Use the Import Data Wizard to import a Streets and Trips 2000 Pushpin set
	     to your map. To start the Import Data Wizard, click Import Data on the
	     File menu.
	
	     -or-
	
	   - Create the Pushpin set. To do this, follow these steps:
	
	     a. To create a new Pushpin, click Pushpin on the Drawing toolbar.
	
	     b. Click the exact location on the map where you want to place the
	        Pushpin.
	
	     c. In the gray bar of the text balloon, double-click Untitled, and then
	        type a title for your Pushpin.
	
	     d. In the white bar of the text balloon, type the text that you want to
	        add (if any) to the Pushpin note.
	
	     e. Click X in the upper-right corner of the text balloon to close it.
	
	     f. Repeat steps a through e to create the Pushpins that you want to
	        display on the map.
	
	The Pushpins that you create are placed in the My Pushpins set by default.
	
	3. Group the Pushpins into the Pushpin sets that you want.
	
	  NOTE: Pushpins that are imported from external files can only be moved into
	  empty Pushpin sets or sets that contain Pushpins from the same source.
	
	  On the map, right-click the Pushpin that you want to move, click Properties,
	  and then do any of the following:
	
	   - To move a pushpin to an existing Pushpin set, click the data set to which
	     you want to move the Pushpin under "Data set name", and then click OK.
	
	     -or-
	
	   - To move a Pushpin to a new data set, click New Data Set, then type a name
	     for the new data set, and then click OK twice.
	
	4. Click Save on the File menu.
	
	5. In the Save As dialog box that appears, specify a name and location where you
	  want to save your master map, and then click Save.
	
	Create New Maps Based on the Master Map:
	
	When you want to view a particular pushpin set, open the master map, and then
	remove the Pushpin sets that you do not want to display on the map. To do this,
	follow these steps:
	
	1. Start Streets and Trips, and open the master map that you created.
	
	2. Under Pushpins, in the "Legend and Overview" pane, right-click the Pushpin
	  set(s) that you want to remove, and then click Delete.
	
	3. Click Save on the File menu.
	
	4. In the Save As dialog box that appears, specify a name and location where you
	  want to save your new map, and then click Save.
	
	Method 3: Import a Specific List of Addresses to Your Map
	---------------------------------------------------------
	
	If you are importing addresses to your map from another program such as Excel,
	create separate worksheets that contain a specific list of addresses for each
	Pushpin set that you want to create. You can then use the Import Data Wizard to
	import the list of addresses that you want to your map. To start the Import Data
	Wizard, click Import Data on the File menu.
	
	MORE INFORMATION
	================
	
	For more information about how to create and work with pushpins and pushpin
	sets, click "Microsoft Streets & Trips Help" on the Help menu, click the
	Answer Wizard tab, type "pushpin" (without the quotation marks), and then click
	Search to view the topics returned.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbimu 
	Technology        : kbHomeProdSearch kbExpediaSearch kbExpediaStreets2001
	Version           : :
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
