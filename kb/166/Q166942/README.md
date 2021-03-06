---
layout: page
title: "Q166942: WD97: Bullets and Numbers Styles Convert Incorrectly to 6.x/7.x"
permalink: /kb/166/Q166942/
---

## Q166942: WD97: Bullets and Numbers Styles Convert Incorrectly to 6.x/7.x

{% raw %}

	Article: Q166942
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbother kbnumbering
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you create a document in Word 97 containing text formatted for bullets or
	numbering, when you open the document in Word 6.0 or Word 7.0 (95), the
	"Distance from text" for the bulleted or numbered text has changed from the
	original distance from text created in Word 97.
	
	For example, the following bulleted list
	
	  * Line one
	    * Line two
	      * Line three
	
	will result with an increased bullet-to-text indent when the file is opened in
	Word 6.0 or Word 7.0 as follows:
	
	  * Line one.
	    *       Line two
	      *             Line three
	
	NOTE: This problem occurs regardless of whether you save the document as Word
	6.0/95 or if you open the Word 97 document in either Word 6.0 or Word 7.0.
	
	CAUSE
	=====
	
	The bulleted or numbered text has been formatted using any of the List Bullet or
	List Number styles.
	
	WORKAROUND
	==========
	
	Instead of using the List Bullet or List Number styles, format your text using
	the bullets and numbering commands (on the Format menu or the Formatting
	toolbar). Then, apply indentation using the Increase Indent or Decrease Indent
	toolbar buttons.
	
	MORE INFORMATION
	================
	
	In order to open a Word 97 document in an earlier version of Word (6.x and 7.x),
	you must use a converter.
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q162214 WD: How to Obtain the Word 97 Converter
	
	Additional query words:
	
	======================================================================
	Keywords          : kbother kbnumbering 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
