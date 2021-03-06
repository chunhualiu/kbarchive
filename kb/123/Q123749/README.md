---
layout: page
title: "Q123749: How the TCP Push Bit Was Changed for Windows NT 3.5"
permalink: /kb/123/Q123749/
---

## Q123749: How the TCP Push Bit Was Changed for Windows NT 3.5

{% raw %}

	Article: Q123749
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5,4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 4.0 
	- Microsoft Windows NT Server versions 3.5, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The TCP/IP stack for Windows NT version 3.5 was completely redesigned. This
	article covers one of the many performance enhancements implemented; the
	improved handling of the TCP PUSH bit on the receive end.
	
	MORE INFORMATION
	================
	
	The TCP protocol has a bit in every header called the PUSH bit. RFC 1122 section
	4.2.2.2 contains the following text on the PUSH bit.
	
	  4.2.2.2  Use of Push: RFC-793 Section 2.8
	
	     When an application issues a series of SEND calls without
	     setting the PUSH flag, the TCP MAY aggregate the data
	     internally without sending it. Similarly, when a series of
	     segments is received without the PUSH bit, a TCP MAY queue
	     the data internally without passing it to the receiving
	     application.
	
	     The PUSH bit is not a record marker and is independent of
	     segment boundaries. The transmitter SHOULD collapse
	     successive PUSH bits when it packetizes data, to send the
	     largest possible segment.
	
	     A TCP MAY implement PUSH flags on SEND calls. If PUSH flags
	     are not implemented, then the sending TCP: (1) must not
	     buffer data indefinitely, and (2) MUST set the PUSH bit in
	     the last buffered segment (i.e., when there is no more
	     queued data to be sent).
	
	     The discussion in RFC-793 on pages 48, 50, and 74
	     erroneously implies that a received PUSH flag must be passed
	     to the application layer. Passing a received PUSH flag to
	     the application layer is now OPTIONAL.
	
	     An application program is logically required to set the PUSH
	     flag in a SEND call whenever it needs to force delivery of
	     the data to avoid a communication deadlock. However, a TCP
	     SHOULD send a maximum-sized segment whenever possible, to
	     improve performance (see Section 4.2.3.4).
	
	     DISCUSSION:
	        When the PUSH flag is not implemented on SEND calls,
	        i.e., when the application/TCP interface uses a pure
	        streaming model, responsibility for aggregating any
	        tiny data fragments to form reasonable sized segments
	        is partially borne by the application layer.
	
	        Generally, an interactive application protocol must set
	        the PUSH flag at least in the last SEND call in each
	        command or response sequence. A bulk transfer protocol
	        like FTP should set the PUSH flag on the last segment
	        of a file or when necessary to prevent buffer deadlock.
	
	        At the receiver, the PUSH bit forces buffered data to be
	        delivered to the application (even if less than a full
	        buffer has been received). Conversely, the lack of a
	        PUSH bit can be used to avoid unnecessary wakeup calls
	        to the application process; this can be an important
	        performance optimization for large timesharing hosts.
	        Passing the PUSH bit to the receiving application allows
	        an analogous optimization within the application.
	
	The receive-side use of the PUSH bit was changed in Windows NT version 3.5. In
	Windows NT version 3.1, TCP/IP behaved as if the PUSH bit was always set by the
	sender. Consequently, it completed application recv() calls as soon as any data
	was available. In Windows NT version 3.5, the receive logic was optimized to use
	the PUSH bit. This reduces the number of times an application has to wake up for
	incoming data. However, when NT is communicating with a TCP/IP implementation
	(or application) that does not set the PUSH bit at appropriate times,
	performance can suffer.
	
	Performance degrades because, when data arrives without the PUSH bit set, TCP
	holds onto the application's recv() while waiting for the rest of the data.
	Windows NT version 3.5 TCP/IP completes a recv() call when:
	
	- Data arrives with the PUSH bit set.
	
	  -or-
	
	- The user recv() buffer is full.
	
	  -or-
	
	- 0.5 seconds have elapsed since any data arrived.
	
	When the third complete test above is required to complete a recv() call,
	performance degrades.
	
	The following example shows how the improved handling of the TCP PUSH bit can
	improve performance:
	
	  A client-server pair is going to transfer 4096 bytes between them on
	  Ethernet. The client application executes a send() for 4096 bytes.
	  Windows NT TCP/IP breaks the 4096 bytes into three Ethernet packets:
	
	     1460 bytes, no PUSH
	     1460 bytes, no PUSH
	     1176 bytes, PUSH is set
	
	  At the same time, the server executes recv(), for 8192 bytes. When the
	  first packet arrives, TCP puts the data into the user buffer. The same
	  thing happens for the second packet since PUSH is still not set.
	  However, when the third packet arrives, TCP completes the recv() because
	  PUSH was set.
	
	In this scenario, holding on to the recv() boosts performance because of the
	overhead implicit in each recv() call; instead of making three calls to recv(),
	the application makes only one, returning all 4096 bytes. If the client did not
	set the PUSH flag on the third packet, TCP would not send recv() for another 0.5
	seconds. Because some TCP/IP implementations (and applications) never set PUSH,
	they tend to perform poorly with Windows NT version 3.5 TCP/IP.
	
	
	Additional query words: RFC1122 sec prodnt performance application sockets winsock
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS350 kbWinNTS350search
	Version           : winnt:3.5,4.0
	
	=============================================================================
	

{% endraw %}
