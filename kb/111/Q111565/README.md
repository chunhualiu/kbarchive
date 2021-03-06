---
layout: page
title: "Q111565: How to Create a Trust Relationship from One Computer"
permalink: /kb/111/Q111565/
---

## Q111565: How to Create a Trust Relationship from One Computer

{% raw %}

	Article: Q111565
	Product(s): Microsoft Windows NT
	Version(s): 3.1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Advanced Server, version 3.1 
	-------------------------------------------------------------------------------
	
	A trust relationship is a link between two different domains, where one
	domain honors the users of another domain, trusting that other domain to
	authenticate the accounts of its own users.
	
	There are normally two steps required to create a trust relationship.
	First, one domain must permit a second domain to trust it. Then the second
	domain must be set to trust the first domain. Because the trust
	relationship is not yet established, these two steps often need to be
	performed by separate administrators. There are other ways to establish
	trust relationships.
	
	One way requires only that an identical user account with administrative
	privileges be created on both domains. This might be an option for those
	network administrators who have identical passwords for all the
	administrative accounts or, at least, know the passwords and can change
	them while setting up the trust relationship.
	
	NOTE: Keep in mind that creating duplicate accounts on different domains
	defeats the purpose of having one account for the whole network, which is
	one of the key features of Windows NT Advance Server networks. Changes made
	to one account must be changed on the other domain as well.
	
	Procedure for Setting Up a Trust Relationship from One Computer
	---------------------------------------------------------------
	
	For this procedure assume there two domains, A and B. You are currently
	logged onto domain A which will be the trusting domain. Domain B will be
	the trusted domain. To set up the trust relationship from a single
	computer, perform the following steps:
	
	1. Create an identical user name and password on both domains with domain
	  administrative rights.
	
	2. Make sure you are logged onto domain A.
	
	3. From User Manager for Domains (note the title bar displays "User Manager -
	  A"), choose Select Domain from the User menu. Type B (the title bar now
	  displays "User Manager - B").
	
	4. From the Policy menu, choose Trust Relationship. Choose Add and type A. Enter
	  a password that you will use on domain A to trust domain B. Domain A should
	  now be listed under Permitted to Trust this Domain. Close the Trust
	  Relationship dialog box.
	
	5. From the User menu choose Select Domain and type A. The title bar should read
	  "User Manager - A."
	
	6. From the Policy menu, choose Trust Relationship. Add domain B and use the
	  same password you used in Step 4.
	
	  A dialog box appears notifying you, "Trust relationship with B successfully
	  established."
	
	REFERENCES
	==========
	
	System Guide for Microsoft Windows NT Advanced Server, chapter 13 "User
	
	  Manager for Domains"
	
	Additional query words: prodnt
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTAdvSerSearch kbWinNTAdvServ310 kbWinNT310Search
	Version           : 3.1
	
	=============================================================================
	

{% endraw %}
