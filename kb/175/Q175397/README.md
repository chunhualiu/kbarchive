---
layout: page
title: "Q175397: Shared Folders Gateway Should Check If Path Uses Long Filenames"
permalink: /kb/175/Q175397/
---

## Q175397: Shared Folders Gateway Should Check If Path Uses Long Filenames

{% raw %}

	Article: Q175397
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0 SP1,3.0 SP2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0 SP1, 3.0 SP2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to save files to a shared folder and using long filenames, an
	access violation in Sfgw.exe can occur.
	
	CAUSE
	=====
	
	While the Shared Folders Gateway (SFGW) installable file system notifies the
	system that it does not support long filenames, a file system request was still
	reaching SFGW containing a reference to a long filename. Because SFGW was not
	expecting such a filename, an access violation occurred while processing this
	filename.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server version 3.0, 3.0
	Service Pack 1, and 3.0 Service Pack 2.
	
	This problem was corrected in the latest SNA Server version 3.0 U.S. Service
	Pack. For information on obtaining this Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	MORE INFORMATION
	================
	
	A Drwtsn32.log will contain information similar to the following:
	
	Application exception occurred:
	       App: sfgw.dbg (pid=188)
	       When: 10/7/1997 @ 9:45:16.800
	       Exception number: c0000005 (access violation)
	
	function: find_rcb
	       00a72efd eb08             jmp     find_rcb+0x27 (00a72f07)
	       00a72eff a198fba800       mov    eax,[vcbptr (00a8fb98)]
	ds:00a8fb98=0b7a1b70
	       00a72f04 8b4854           mov     ecx,[eax+0x54]
	ds:00bde966=????????
	       00a72f07 a19cfba800       mov   eax,[tpcbptr (00a8fb9c)]
	ds:00a8fb9c=00094388
	       00a72f0c 890da0fba800     mov    [rcbptr (00a8fba0)],ecx
	ds:00a8fba0=000ab008
	       00a72f12 8b4008           mov     eax,[eax+0x8]
	ds:00bde966=????????
	       00a72f15 85c0             test    eax,eax
	       00a72f17 741e             jz      find_rcb+0x57 (00a72f37)
	       00a72f19 3905a0fba800     cmp    [rcbptr (00a8fba0)],eax
	ds:00a8fba0=000ab008
	       00a72f1f 7407             jz      find_rcb+0x48 (00a72f28)
	FAULT ->00a72f21 8b4004           mov     eax,[eax+0x4]
	ds:00bde966=????????
	       00a72f24 85c0             test    eax,eax
	       00a72f26 75f1             jnz     find_rcb+0x39 (00a72f19)
	       00a72f28 85c0             test    eax,eax
	       00a72f2a 740b             jz      find_rcb+0x57 (00a72f37)
	       00a72f2c a1a0fba800       mov    eax,[rcbptr (00a8fba0)]
	ds:00a8fba0=000ab008
	       00a72f31 80780809         cmp     byte ptr [eax+0x8],0x9
	ds:00bde966=??
	       00a72f35 751f             jnz     find_rcb+0x76 (00a72f56)
	       00a72f37 c7052cffa80000000002
	ds:00a8ff2c=00000000
	                                 mov   dword ptr [secondary_rc
	(00a8ff2c)],0x2000000
	       00a72f41 66c70528ffa8000001
	ds:00a8ff28=0000
	                                 mov     word ptr [primary_rc
	(00a8ff28)],0x100
	       00a72f4a 33c0             xor     eax,eax
	       00a72f4c a39cfba800       mov   [tpcbptr (00a8fb9c)],eax
	ds:00a8fb9c=00094388
	
	*----> Stack Back Trace <----*
	
	FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function Name
	0bacfcf8 00a6245c 0b7a1b70 00000000 00000374 00000000 WAPPC32!find_rcb
	(FPO: [0,0,0])
	0bacfd0c 00a611fc 0006d403 007b2860 60201260 00000374
	WAPPC32!init_verb_checks  (FPO: [1,1,3])
	0bacfe24 00a610d2 0b7a1b70 00000003 00000374 0b7a1b70 WAPPC32!Appc_Main
	(FPO: [EBP 0x007b2860] [3,64,4])
	0bacfe38 0100ad12 00000374 0b7a1b70 60201260 0b7a1920
	WAPPC32!WinAsyncAPPCEx  (FPO: [2,0,1])
	0bacfe50 0100250d 0b7a1b70 00000374 00000000 60201260 sfgw!<nosymbols>
	(FPO: [3,0,3])
	0bacfe68 01002621 007b2948 0000004b 00000003 0100336a sfgw!<nosymbols>
	(FPO: [3,0,2])
	0bacfe78 0100336a 007b2948 0000004b 00a61f39 00a7a010 sfgw!<nosymbols>
	(FPO: [2,0,0])
	0bacffa4 01003b7e 00a61f39 00a7a010 0bacffec 0b7a1920 sfgw!<nosymbols>
	(FPO: [EBP 0x00a61f39] [0,68,4])
	0bacffb8 77f46c2e 0b7a1920 00a61f39 00a7a010 0b7a1920 sfgw!<nosymbols>
	(FPO: [EBP 0x00a61f39] [1,0,4])
	00a61f39 000178b9 5f5dc68b c4815b5e 00000100 8d000cc2 kernel32!<nosymbols>
	
	Additional query words: shared folders sfgw
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ300SP1 kbSNAServ300SP2
	Version           : WINDOWS:3.0,3.0 SP1,3.0 SP2
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
