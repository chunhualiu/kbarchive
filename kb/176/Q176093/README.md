---
layout: page
title: "Q176093: Gridtest.exe Sample Grid Does Not Refresh Properly"
permalink: /kb/176/Q176093/
---

## Q176093: Gridtest.exe Sample Grid Does Not Refresh Properly

{% raw %}

	Article: Q176093
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbfile kbsample kbDesigner kbvfp500 kbvfp600 kbDSupport
	Last Modified: 11-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Gridtest.exe contains an example that demonstrates using a grid based on two
	data sources. The sample shows that the grid may not display properly when you
	navigate the master table with a custom toolbar while the focus on the main form
	is in the grid.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  Gridtest.exe
	  (http://download.microsoft.com/download/vfox60/problem/1/W9X/EN-US/Gridtest.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	Symptoms
	--------
	
	Under the following conditions, a grid based on two tables will not display the
	correct data:
	
	- Focus is on the grid making one of the grid cells active.
	
	- A toolbar button that skips to the next or previous record is clicked.
	
	- The number of records in the grid exceeds the number of records that may be
	  displayed.
	
	- The grid is scrolled.
	
	Whether or not the scroll thumb or the scroll arrows are used to scroll the grid
	determines how the data is misrepresented. In either case, the records from the
	second table are misrepresented.
	
	Resolution
	----------
	
	Here are two possible workarounds:
	
	- In the Click events of the navigation buttons on the toolbar, set the focus
	  on the main form to an object other than the grid. This is demonstrated in
	  the sample file with the form called Works. An example of the code is as
	  follows:
	
	        _SCREEN.ACTIVEFORM.txtF1.SETFOCUS
	         SELECT TBL1
	         SKIP 1
	        _SCREEN.ACTIVEFORM.REFRESH
	
	  (txtF1 is the name of a visible object on the form)
	
	-or-
	
	- Create a button on the main form that executes the following code:
	
	        THISFORM.GRID1.REFRESH
	
	  (Grid1 is the name of the grid)
	
	  Executing the refresh from a button on the custom toolbar does not solve the
	  problem.
	
	  See step 6 under Steps to Reproduce Behavior for this workaround.
	
	NOTE: If the navigation buttons are objects on the form, this problem does not
	occur.
	
	Status
	------
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Using the sample file run the form named Broken.
	
	2. Click the Next button located on the form. All the visible cells in the first
	  column of the grid should contain the number 2. Note that if the grid is
	  scrolled with either the scroll thumb or scroll arrows, all the grid columns
	  display correctly. The example below demonstrates how the data should be
	  displayed in the grid. The last row will not be visible.
	
	     TBL2.F1   TBL2.F2   TBL3.F2   TBL3.F3
	     -----------------------------------------
	
	     2         a         a         Red
	     2         b         b         Blue
	     2         c         c         Green
	     2         d         d         Yellow
	     2         e         e         Brown
	
	3. Click in any cell of the grid. The grid now has focus on the form.
	
	4. Click the Previous button on the Toolbar, not the form.
	
	5. Scroll down the grid with the scroll thumb or slider. All the records in the
	  third column (TBL3.F2) will contain the letter "a." "Red" appears in all the
	  records of the fourth column (TLB3.F3).
	
	  Scroll down the grid with the scroll arrow. All the records in the third
	  column (TBL3.F2) will contain the letter "d." "Yellow" appears in all the
	  records of the fourth column (TLB3.F3).
	
	  Using the scroll thumb, scroll arrows, or clicking in one of the grid cells
	  does not cause that cell to refresh properly.
	
	  NOTE: The results of this step may be inconsistent and differ from what is
	  described here. What should be displayed is the example shown in step 2 above
	  with the number 1 in the first grid column for all rows.
	
	6. Make sure that the focus is not in either the third or fourth grid column,
	  and then click the Grid Refresh button on the form. The grid should now be
	  back to normal. If one of the cells in the third or fourth column had focus,
	  it will not refresh, but all the others will. This step implements the second
	  workaround described in the Resolution section above.
	
	7. Click in one of the grid cells, and then click the Next button on the
	  toolbar. The grid should move so that the number 2 is in the first column
	  (TBL2.F1). The data in the third and fourth columns should be correct. Refer
	  to the grid in step 2 above. Note that the last row is not visible.
	
	8. Scroll the grid using the down scroll arrow. Note the values in the third and
	  fourth columns for the first visible record when you finish scrolling.
	
	  If the scroll down was stopped, with only the last two records displayed, and
	  then the up scroll arrow is clicked, all the records displayed from TBL3 will
	  have the correct information. The example below demonstrates how the data
	  should be displayed in the grid.
	
	     TBL2.F1   TBL2.F2   TBL3.F2   TBL3.F3
	     --------------------------------------
	
	     2         a         d         Yellow
	     2         b         d         Yellow
	     2         c         d         Yellow
	     2         d         d         Yellow
	     2         e         e         Brown
	
	  If only the last record was visible when scrolling down stopped, then all the
	  records will contain an "e" in the third column (TBL3.F2) and "Brown" in the
	  fourth column (TBL3.F3) of the grid when scrolling up.
	
	9. Modify the GridTtest.pjx sample project and examine the code in the forms and
	  visual classes.
	
	Additional query words: Gridtest Grid Display
	
	======================================================================
	Keywords          : kbfile kbsample kbDesigner kbvfp500 kbvfp600 kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : WINDOWS:5.0,5.0a,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
