---
layout: page
title: "Q166497: WD97: Error Using Border Constants with Font.Borders"
permalink: /kb/166/Q166497/
---

## Q166497: WD97: Error Using Border Constants with Font.Borders

{% raw %}

	Article: Q166497
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kberrmsg kbdta kbdtacode word8 word97
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you attempt to apply borders to selected characters using Microsoft Visual
	Basic for Applications, the following error occurs:
	
	  Run-time error '5941': The requested member of the collection does not exist.
	
	CAUSE
	=====
	
	By design, character borders will only take 1 or the wdBorderTop constant as
	arguments because the character borders count equals 1.
	
	For example, the following Visual Basic for Applications commands will cause the
	error to occur if you attempt to designate a right border for a selected
	character:
	
	     Selection.Font.Borders(wdBorderRight).LineStyle _
	     =WdLineStyleThickThinSmallGap
	
	WORKAROUND
	==========
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	To work around this problem, use either of the following lines of code to apply
	the border style to a selected character:
	
	     Selection.Font.Borders(1).LineStyle = WdLineStyleThickThinSmallGap
	
	-or-
	
	     Selection.Font.Borders(wdBorderTop).LineStyle = _
	     WdLineStyleThickThinSmallGap
	
	MORE INFORMATION
	================
	
	For additional information, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q173707 OFF97: How to Run Sample Code from Knowledge Base Articles
	
	
	REFERENCES
	==========
	
	For more information about getting help with Visual Basic for Applications,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q163435 VBA: Programming Resources for Visual Basic for Applications
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.
	
	Additional query words: wordcon vb vba vbe
	
	======================================================================
	Keywords          : kberrmsg kbdta kbdtacode word8 word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
