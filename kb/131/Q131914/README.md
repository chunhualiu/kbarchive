---
layout: page
title: "Q131914: PC Gen: Using the DEC Redirector Slows Mail"
permalink: /kb/131/Q131914/
---

## Q131914: PC Gen: Using the DEC Redirector Slows Mail

{% raw %}

	Article: Q131914
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.2,3.2a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, versions 3.2, 3.2a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the DEC redirector to connect to a Pathworks server that has the
	version 3.2 or 3.2a Microsoft Mail for PC Networks database, and the mail
	message file (MMF) is stored on the server, Microsoft Mail for Windows runs
	extremely slowly when you send or receive messages.
	
	CAUSE
	=====
	
	Mail accesses the MMF by using byte range locking, so to send or receive a
	message, it attempts to lock a byte range on the MMF, even if it already has a
	lock on that byte range. The Pathworks server handles multiple byte range locks
	on the same range as a file lock violation, even when the lock comes from the
	same workstation. When the server rejects the lock, the redirector attempts
	three more times to establish the lock, and succeeds on the last attempt. This
	creates a delay while Mail waits for the redirector to establish the lock.
	
	The Pathworks server also adds to the delay by increasing the response delay when
	multiple file lock violations occurs on a file. Between the redirector trying
	four times and the server waiting longer and longer between these attempts to
	respond to the workstation, Mail effectively stops running for 4 to 10 seconds
	per message.
	
	RESOLUTION
	==========
	
	This is not a problem with Mail but with the underlying network architecture.
	
	The resolution can be one of the following:
	
	- Move the MMF files to the local workstation.
	
	- Upgrade the Pathworks server to version 5.0, and use the DEC redirector
	  version 5.0 in enhanced mode.
	
	- Upgrade Microsoft Windows version 3.1 to Microsoft Windows for Workgroups
	  3.11, and use the enhanced redirector.
	
	MORE INFORMATION
	================
	
	Testing shows that the problem occurs primarily when you use Pathworks version
	4.1, the DEC redirector version 4.1a, and Windows version 3.1; it can also occur
	when you run the DEC redirector version 5.0 in basic mode.
	
	The following table summarizes the results of testing:
	
	Client OS                     Redir    Mode         Server   Result
	-----------------------------------------------------------------------
	Windows 3.1                   4.1a     basic        4.1      failed (1)
	Windows 3.1                   4.1a     enhanced     4.1      failed (1)
	Windows for Workgroups 3.11   4.1a     enhanced     4.1      OK (2)
	Windows 3.1                   4.1a     enhanced     NTAS 3.5 OK (3)
	Windows 3.1                   5.0      enhanced     4.1      failed (1)
	Windows 3.1                   5.0      basic        5.0      failed (1)
	Windows 3.1                   5.0      enhanced     5.0      OK (4)
	Windows for Workgroups 3.11   5.1      enhanced     5.0      OK (5)
	Windows for Workgroups 3.11   5.1      enhanced     5.0      OK (5)
	
	Notes:
	
	- (1) 4 lock violations per message
	
	- (2) file lock broken and file relocked, no violation
	
	- (3) 1 lock violation.
	
	- (4) 1 lock violation. Response from server was slow (~520 ms).
	
	- (5) No file locks were made
	
	Additional query words: 3.20 slow
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailPCN320 kbMailPCN320a
	Version           : WINDOWS:3.2,3.2a
	
	=============================================================================
	

{% endraw %}
