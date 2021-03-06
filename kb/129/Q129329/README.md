---
layout: page
title: "Q129329: HOWTO: Populate a Form's List Box Object from an Array"
permalink: /kb/129/Q129329/
---

## Q129329: HOWTO: Populate a Form's List Box Object from an Array

{% raw %}

	Article: Q129329
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b,5.0,6.0
	Operating System(s): 
	Keyword(s): kbDesigner kbvfp300 kbvfp500 kbvfp600
	Last Modified: 25-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows how to populate a ListBox object from an array.
	
	MORE INFORMATION
	================
	
	In Visual FoxPro, in addition to the usual single-column list, you can now have
	multiple-column lists. Additionally, the ListBox object also supports the
	multiple-select and mover capabilities.
	
	The ListBox object has several properties that control the displayed output. Some
	of these properties are covered in this article. For more information, please
	see Chapter 11 of the Developer's Guide or the "ListBox Control" topic in the
	Help menu.
	
	ListBox Control Properties and Display Attributes
	-------------------------------------------------
	
	The following two tables describes several of the data properties and display
	attributes of the ListBox control:
	
	Data Property    Description
	----------------------------------------------------------------
	ColumnCount      Number of columns contained in the ListBox object.
	
	RowSource        Source of the values displayed in the ListBox object.
	
	RowSourceType    Data type of the values. For example, fields, array, list,
	                files, and list of fields are all valid data types.
	
	ControlSource    Where the value chosen by the user is stored. For example,
	                the value may be stored in a variable.
	
	BoundColumn      The column of a multiple-column array to return when the
	                user selects an object from the ListBox object.
	
	Display
	Attribute        Description
	---------------------------------------------------------------------
	Moverbars        Allows the rearrangement of values displayed in the
	                ListBox object.
	
	Multiselect      Allows users to choose multiple items from the
	                ListBox object.
	
	FontName         The font used in displaying the ListBox control's data.
	
	FontItalic       Turns on italic mode for the font specified in the
	                FontName property.
	
	Step-by-Step Example
	--------------------
	
	The following steps show how to create and add an array-driven ListBox to a
	form.
	
	1. In the Command window, type:
	
	  CREATE FORM LISTTEST
	
	2. Adjust the form size so you have some working room. Click the form to select
	  it. Then right-click to bring up the Form sub-menu.
	
	3. Select the Data Environment menu pad. Right-click the Data Environment
	  window, and choose Add. In the Add Table or View dialog, choose Other. From
	  the SAMPLES\DATA directory, choose Customer, and click OK in the Open dialog
	  box. The Customer table should now be in the data environment for the form.
	  You can close the Data Environment for this form.
	
	4. From the Form menu, choose New Property. Type in the array name as
	  "MYARRAY(1)" (without the quotation marks). The array will now become a new
	  property of the form. For more information on adding properties scoped to a
	  form or form set, please see the topic "properties, scoped to form sets" in
	  the Help menu.
	
	5. If the Form Properties sheet is not already on the screen, click the form to
	  select it. Then right-click to bring up the property sheet.
	
	  a. Choose the Methods tab for the Form Properties sheet.
	
	  b. Place the following SQL statement in the Form Load event:
	
	  SELECT cust_id, contact, phone FROM customer
	  INTO ARRAY Thisform.myarray
	
	  NOTE: The prefix "Thisform" in front of the array name is a Critical and
	  subtle point to remember about the scoping of member arrays and variables
	  within a form. If the SELECT statement is simply done INTO ARRAY myarray, the
	  array created by the SQL statement will not have scope within the form
	  itself. By prefacing the array name with the "Thisform" clause, the results
	  of the SQL statement are directed into the array named myarray, which is part
	  of the form definition.
	
	  c. Close the FORM1.LOAD screen.
	
	6. From the Form Controls toolbar, click the ListBox object and drag the ListBox
	  object onto the new form. Size the ListBox to occupy most of the screen.
	
	7. With the ListBox selected, right-click the ListBox object, and choose
	  Properties.
	
	8. Select the Data tab, and set the following properties:
	
	  - BoundColumn = 1
	
	  This property governs which column of a multiple-element array is returned to
	  the List1.Value data element when a user selects a record in the ListBox. In
	  this example, you are creating a three-column array, so you can use a value
	  of 1, although 2 or 3 are also valid entries for this property.
	
	  - NumberOfElements=ALEN(THISFORM.MYARRAY,1)
	
	  This property governs the total number of elements that will be displayed in
	  the ListBox. It is valid only for a RowSourceType of 5. By using the
	  =ALEN(THISFORM.MYARRAY,1) expression, you are telling FoxPro to display all
	  the values in the array as opposed to limiting how many elements are
	  displayed. Note that you must type the leading equals sign.
	
	  The following information from the Visual FoxPro Help menu explains the
	  second, optional parameter used by the ALEN() function:
	
	  The second property of the ALEN() determines if ALEN() returns the number of
	  elements, rows or columns in the array. nArrayAttribute can be 0, 1, or 2:
	
	  a. 0 specifies to return the number of elements in the array. Omitting
	     nArrayAttribute is identical to specifying 0.
	
	  b. 1 specifies to return the number of rows in the array.
	
	  c. 2 specifies to return the number of columns in the array. If the array is
	     a one-dimensional array, ALEN() returns 0 (no columns).
	
	  - RowSource = THISFORM.MYARRAY
	
	  This RowSource property tells Visual FoxPro that the data will be coming from
	  an object called MYARRAY.
	
	  - RowSourceType = 5 - Array
	
	  This RowSourceType property tells Visual FoxPro that the type of object that
	  contains the data is an array.
	
	9. From the ListBox Properties sheet, select the Layout tab, and set the
	  following properties:
	
	  - ColumnCount=3
	
	  This property governs how many elements of the array will be displayed.
	  Because the array that will drive this ListBox contains three columns, the
	  value of 3 is used. Array elements are displayed in the order they appear in
	  the array. For example, say you issue an SQL SELECT statement such as this:
	
	  SELECT cust_id, contact, phone FROM CUSTOMER
	
	  Then the data in the ListBox will be displayed in that order (cust_id,
	  contact, phone).
	
	  - ColumnLines = .T.
	
	  This property determines whether or not to display bars between the columns
	  displayed in the array.
	
	  NOTE: Column lines are represented on the form during design time as vertical
	  bars. Because this is both a run-time and design-time property, if this value
	  is set to false, there will be NO visual indicator of the number of columns
	  defined for the ListBox object.
	
	  - ColumnWidths = 60,220,90
	
	  By default, the pixel is the unit of measurement on a Form.
	
	10. From the ListBox Properties sheet, select the Methods tab. Double-click the
	  word [Default] next to the words DblClick Event. This should open up an
	  editing window for the DblClick event.
	
	  In the editing window, type this command:
	
	  =MESSAGEBOX(THISFORM.LIST1.VALUE,64)
	
	  When you double-click an item in the list, your selection will be shown in a
	  message box with an OK button.
	
	11. Place a CommandButton control on the form. Place the following command in
	  the CLICK event:
	
	  RELEASE THISFORM
	
	  Change the caption to Quit.
	
	12. Save and run your form.
	
	To get a feel for changing some of the properties on an active form, you might
	want to try some of the following commands in the Command window:
	
	        LISTTEST.LIST1.MultiSelect=.T.      && Turn on multiselect property.
	        LISTTEST.LIST1.FontName="MS Sans Serif"  && Change font for ListBox.
	        LISTTEST.LIST1.FontItalic=.T.          && Make the text italic.
	        LISTTEST.List1.BoundColumn=3           && Alter what column's data is
	                                           && returned to List1.Value.
	                                           && When you change this and then
	                                           && double-click a record, the
	                                           && data from the third column will
	                                           && be returned to LIST1.VALUE.
	
	Additional query words: Multiselect multicolumn multi-select multi-column
	
	======================================================================
	Keywords          : kbDesigner kbvfp300 kbvfp500 kbvfp600 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600
	Version           : WINDOWS:3.0,3.0b,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
