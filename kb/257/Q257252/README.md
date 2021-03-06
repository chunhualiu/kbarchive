---
layout: page
title: "Q257252: XADM: Default Registry Entries for Exchange Server Info Store"
permalink: /kb/257/Q257252/
---

## Q257252: XADM: Default Registry Entries for Exchange Server Info Store

{% raw %}

	Article: Q257252
	Product(s): Microsoft Exchange
	Version(s): 5.5
	Operating System(s): 
	Keyword(s): exc55
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article provides details about the registry settings that are used by the
	Microsoft Exchange Server Information Store service. The information store
	registry values that are noted in this article are present by default after you
	successfully set up Exchange Server 5.5.
	
	When you run Exchange Performance Optimizer, some of these default values may
	change, depending on the options that you choose. When you run the "perfwiz -v"
	(without quotation marks) command from a command prompt at the \Exchsrvr\Bin
	folder, you can modify these default values. If you manually specify a value
	that is outside of the minimum or maximum value, the minimum or maximum value is
	used, respectively. When you use the "perfwiz -r" command, you can open
	Performance Optimizer in read-only mode to view the current settings. This does
	not stop Exchange Services.
	
	MORE INFORMATION
	================
	
	The information store registry values are in the following format:
	
	  Name
	  Type
	  Default Value
	
	Information store registry values are present in Registry Editor (Regedt32.exe)
	under the following location:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\
	  MSExchangeIS\ParametersSystem
	
	These information store registry values are the following:
	
	  Background Threads
	  REG_DWORD
	  0x25
	
	  Buffer Threshold High Percent
	  REG_DWORD
	  0x3
	
	  Buffer Threshold Low Percent
	  REG_DWORD
	  0x3
	
	  Circular Logging
	  REG_DWORD
	  1
	
	  DB Log Path
	  REG_SZ
	  %s\mdbdata
	
	  DB Recovery
	  REG_DWORD
	  1
	
	  DSA Computer
	  REG_SZ
	  string
	
	  IMAP4 Protocol Log Path
	  REG_SZ
	  %s\mdbdata
	
	  IMAP4 Protocol Logging Level
	  REG_DWORD
	  0
	
	  Max Buffers
	  REG_DWORD
	  0x1f6e
	
	  Max Threads (Public+Private)
	  REG_DWORD
	  5.5 - 0x32
	
	  Minimum Threads
	  REG_DWORD
	  0xa
	
	  MTA Computer
	  REG_SZ
	  string
	
	  NNTP Protocol Log Path
	  REG_SZ
	  %s\mdbdata
	
	  Online Compaction
	  REG_DWORD
	  1
	
	  POP3 Protocol Log Path
	  REG_SZ
	  %s\mdbdata
	
	  POP3 Protocol Logging Level
	  REG_DWORD
	  0
	
	  This Server
	  REG_SZ
	  string
	
	  Working Directory
	  REG_DWORD
	  %s\MDBDATA
	
	Information store registry values are present in Registry Editor (Regedt32.exe)
	under the following location:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\
	  MSExchangeIS\ParametersPrivate
	
	These information store registry values are the following:
	
	  Background Cleanup
	  REG_DWORD
	  60000
	
	  Background Search
	  REG_DWORD
	  0x1388
	
	  DB Path
	  REG_SZ
	  %s\MDBDATA\PRIV.EDB
	
	  Gateway In Threads
	  REG_DWORD
	  0x2
	
	  Gateway Out Threads
	  REG_DWORD
	  0x2
	
	  General Event Log
	  REG_DWORD
	  0
	
	  Track Duplicates
	  REG_DWORD
	  1
	
	  Transport Event Log
	  REG_DWORD
	  0
	
	Information store registry values are present in Registry Editor (Regedt32.exe)
	under the following location:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\
	  MSExchangeIS\ParametersPublic
	
	These information store registry values are the following:
	
	  Background Cleanup
	  REG_DWORD
	  60000
	
	  Background Search
	  REG_DWORD
	  0x1388
	
	  DB Path
	  REG_SZ
	  %s\MDBDATA\PUB.EDB
	
	  General Event Log
	  REG_DWORD
	  0
	
	  Replication Event Log
	  REG_DWORD
	  0
	
	  Track Duplicates
	  REG_DWORD
	  1
	
	  Transport Event Log
	  REG_DWORD
	  0
	
	Information store registry values are present in Registry Editor (Regedt32.exe)
	under the following location:
	
	  HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\
	  MSExchangeIS\ParametersNetif
	
	These information store registry values are the following:
	
	  MaxConcurrency
	  REG_DWORD
	  0
	
	  MaxPoolThreads
	  REG_DWORD
	  0x32
	
	  MinFileKbSec
	  REG_DWORD
	  0x3e8
	
	  NonTFBufferSize
	  REG_DWORD
	  0x1000
	
	  ThreadTimeout
	  REG_DWORD
	  0x15180
	
	  UseAcceptEx
	  REG_DWORD
	  0x1
	
	  UseTransmitFile
	  REG_DWORD
	  0x1
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : :5.5
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
