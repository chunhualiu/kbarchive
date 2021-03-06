---
layout: page
title: "Q175452: Microsoft TCP/IP Training Comments and Corrections"
permalink: /kb/175/Q175452/
---

## Q175452: Microsoft TCP/IP Training Comments and Corrections

{% raw %}

	Article: Q175452
	Product(s): Microsoft Press
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdocfix kbdocerr
	Last Modified: 06-MAR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- MSPRESS Microsoft TCP/IP Training ISBN 1-57231-623-3 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article contains information on known errors, corrections, and comments
	relating to the Microsoft Press book "Microsoft TCP/IP Training," ISBN
	1-57231-623-3.
	
	Contents:
	
	- CD-ROM: RFC793.TXT File Truncated
	
	- Error: Missing Mgmtapi.ddl When Running The Snmputil Utility
	
	- Page 65: Typographic Error
	
	- Page 75: Missing Word
	
	- Page 84: Missing Word
	
	- Page 87: Incorrect Number of Network Addresses Needed
	
	- Page 87: Correction To Subnet Mask (Binary) Address
	
	- Pages 89 & 365: Question Incorrectly Refers To Default Gateway
	
	- Pages 109 & 372: Subnet Mask Not Net Mask
	
	- Page 123: Text Incorrectly Refers To Router B
	
	- Page 180: LMHOSTS Not LMHOST
	
	- Page 218: Text Correction
	
	- Page 242: Incorrect Net Use Syntax
	
	- Page 257: "num" Incorrectly Listed As Top-Level Domain
	
	- Page 258: Missing Punctuation
	
	- Page 267: Incorrect Syntax
	
	- Page 293: Class C IP Address Incorrect
	
	- Page 297: Corrections To Graphic
	
	- Page 299: Step 3, Type The Address For Your WINS Server
	
	- Page 299: Step 5, Type The WINS Server IP Address
	
	- Page 344: Step 1, Copy From CD-ROM Drive
	
	- Page 359: Practice Answers For Page 67 Are Incorrect
	
	- Page 361: Mismatched Answers In Table
	
	- Page 365: Practice Answer Doesn't Match Original Question Asked
	
	- Page 367: Incorrect Explanation For Answer
	
	MORE INFORMATION
	================
	
	CD-ROM: RFC793.TXT File Truncated
	---------------------------------
	
	The file \APPENDIX\RFC793.TXT on the CD-ROM is truncated at page 68. The index at
	the start of this file indicates that there should be 85 pages.
	
	
	Error: Missing Mgmtapi.ddl When Running The Snmputil Utility
	------------------------------------------------------------
	
	When you try to run the Snmputil Utility, found on the CD-ROM under the Course
	Exercise Files link or within the Labfiles directory, you may receive an error
	message similar to the following:
	
	  "The dynamic Link library mgmtapi.dll could not be found in the specified
	  path"
	
	Resolution: Copy Mgmtapi.dll from the TCP/IP Supplemental Course Materials CD-ROM
	(\winnt40.sp2\I386\Mgmtapi.dll) to your Windows NT System32 directory.
	
	
	Page 65: Typographic Error
	--------------------------
	
	Page 65, bullet point 2:
	
	Change:
	"Network 3 represents the WAN conection..."
	
	To:
	"Network 2 represents the WAN connection..."
	
	Page 65, bullet point 3:
	
	Change:
	"Network 3 requires a network ID..."
	
	To:
	"Network 2 requires a network ID..."
	
	
	Page 75: Missing Word
	---------------------
	
	Page 75, sixth paragraph:
	
	Change:
	"...and the ability add new features."
	
	To:
	"...and the ability to add new features."
	
	
	Page 84: Missing Word
	---------------------
	
	Page 84, last sentence:
	
	Change:
	"The number bits in the subnet mask..."
	
	To:
	"The number of bits in the subnet mask..."
	
	
	Page 87: Incorrect Number of Network Addresses Needed
	-----------------------------------------------------
	
	On page 87, in the third paragrah under the Subnetting More Than One Octet
	subheading, change:
	
	"Adding our requirement of subnets, you need at least 16 class B addresses."
	
	To:
	"Adding our requirement of subnets, you need at least 17 class B network
	addresses."
	
	
	Page 87: Correction To Subnet Mask (Binary) Address
	---------------------------------------------------
	
	Page 87, under the Subnetting More Than One Octet subheading:
	
	Change the Subnet Mask (Binary) address from:
	"1111111111 11111111 11111000 00000000"
	
	To:
	"11111111 11111111 11111000 00000000"
	
	
	Pages 89 & 365: Question Incorrectly Refers To Default Gateway
	--------------------------------------------------------------
	
	The question in the middle of pages 89 and 365 should refer to the second
	computer rather than the default gateway.
	
	Change:
	"Why would you not be able to successfully ping your default gateway?"
	
	To:
	"Why would you not be able to successfully ping your second computer?"
	
	
	Pages 109 & 372: Subnet Mask Not Net Mask
	-----------------------------------------
	
	Pages 109 and 372, question 2:
	
	Change:
	"What net mask would be used to supernet this block of numbers?"
	
	To:
	"What subnet mask would be used to supernet this block of numbers?"
	
	
	Page 123: Text Incorrectly Refers To Router B
	---------------------------------------------
	
	Page 123, 2nd paragraph, 2nd sentence:
	
	Change:
	"Router B then evaluates the new entries and updates its routing table, if
	necessary."
	
	To:
	"Router A then evaluates the new entries and updates its routing table, if
	necessary."
	
	
	Page 180: LMHOSTS Not LMHOST
	----------------------------
	
	Page 180, description for the #INCLUDE predefined keyword, second sentence:
	
	Change:
	"Typically, a #INCLUDE file is a centrally located shared LMHOST file."
	
	To:
	"Typically, a #INCLUDE file is a centrally located shared LMHOSTS file."
	
	
	Page 218: Text Correction
	-------------------------
	
	Page 218, under Advanced WINS Server Configuration Options:
	
	Change the description for Backup On Termination from:
	"Specifies that the database will be backed up automatically when WINS Manager is
	closed."
	
	To:
	"Specifies that the database will be backed up automatically when WINS Service is
	stopped, but not when the system is shut down."
	
	
	Page 242: Incorrect Net Use Syntax
	----------------------------------
	
	Page 242, Note, second sentence:
	
	Change:
	"For example, \net use x: \\131.107.2.200\share_name."
	
	To:
	"For example, net use x: \\131.107.2.200\share_name."
	
	
	Page 257: "num" Incorrectly Listed As Top-Level Domain
	------------------------------------------------------
	
	On page 257, under the Top-Level Domains section, it lists num as a top-level
	domain. num is not a top-level domain and should not be included in this list.
	
	
	Page 258: Missing Punctuation
	-----------------------------
	
	Page 258, Zones Of Authority subheading, second paragraph, first sentence:
	
	Change:
	"The name server's zone of authority encompasses at least one domain This
	domain..."
	
	To:
	"The name server's zone of authority encompasses at least one domain. This
	domain..."
	
	
	Page 267: Incorrect Syntax
	--------------------------
	
	Page 267, first example for the primary command:
	
	Change:
	"primary microsoft.com.microsoft.dns"
	
	To:
	"primary microsoft.com microsoft.dns"
	
	
	Page 293: Class C IP Address Incorrect
	--------------------------------------
	
	Page 293, Note, third bullet, example:
	
	Change:
	"(for example: A class C IP address of 229.122.15.88 would have a reverse lookup
	zone name of 15.122.129.in-addr.arpa)."
	
	To:
	"(for example: A class C IP address of 219.122.15.88 would have a reverse lookup
	zone name of 15.122.219.in-addr.arpa)."
	
	
	Page 297: Corrections To Graphic
	--------------------------------
	
	Page 287, graphic:
	
	Three of the four arrows are mislabeled. The arrow pointing from the DNS Server
	to the WINS Server should be labeled 2, the arrow pointing from the WINS Server
	to the DNS Server should be labeled 3, and the arrow pointing from the DNS
	Server to the DNS Client should be labeled 4.
	
	
	Page 299: Step 3, Type The Address For Your WINS Server
	-------------------------------------------------------
	
	On page 299, in the practice section titled "To configure the WINS client, in
	step 3, you will need to type the IP address for your WINS server.
	
	Change:
	"3. In the Primary WINS server box, type the IP address for your DNS server."
	
	To:
	"3. In the Primary WINS server box, type the IP address for your WINS server."
	
	
	Page 299: Step 5, Type The WINS Server IP Address
	-------------------------------------------------
	
	On page 299, in the practice section titled "To configure the WINS resolution,
	you will need to type the IP address for your WINS server in step 5.
	
	Change:
	"5. In the WINS Server box, type the IP address for your DNS server."
	
	To:
	"5. In the WINS Server box, type the IP address for your WINS server."
	
	
	Page 344: Step 1, Copy From CD-ROM Drive
	----------------------------------------
	
	On page 344, step 1 should read:
	
	1. Copy D:\LabFiles\Chapt15\Snmputil.exe to C:\Winnt
	Where D is the drive letter of your CD-ROM drive.
	
	
	Page 359: Practice Answers For Page 67 Are Incorrect
	----------------------------------------------------
	
	On page 359, under the answers listed for page 67, answers "D" and "F" should be
	listed as invalid host IP addresses.
	
	On page 359, change:
	"d. 126.1.0.0
	This is a valid address"
	
	To:
	"d. 126.1.0.0
	This is an invalid address because it falls outside the valid host ID range."
	
	Change:
	"f. 190.7.2.0
	This is a valid address"
	
	To:
	"f. 190.7.2.0
	This is an invalid address because it falls outside the valid host ID range."
	
	Page 66 lists valid host IDs.
	
	
	Page 361: Mismatched Answers In Table
	-------------------------------------
	
	In the middle Practice Answers section on page 361, the answers for "Windows NT
	Workstation computers" and "UNIX workstations" are mismatched. The chart table
	appear as follows:
	
	+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
	| Type of TCP/IP host              | IP address range                                                                                                                    | 
	+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
	| Windows NT Server computers      | Assign high numbers to all servers, for instance 200-250.                                                                           | 
	+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
	| Windows NT Workstation computers | Assign numbers to the Windows NT Workstation computers using a different octet than that used by the servers and UNIX workstations. | 
	+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
	| UNIX workstations                | Assign low numbers to all UNIX workstations, for instance 150-200.                                                                  | 
	+------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
	
	
	Page 365: Practice Answer Doesn't Match Original Question Asked
	---------------------------------------------------------------
	
	On page 365, the second paragraph should be changed to match the original
	question on page 89.
	
	Change:
	"Using the information below, convert your computer's IP address and the IP
	address of your default gateway to binary format, and..."
	
	To:
	"Using the information below, convert your computer's IP address and the IP
	address of your second computer to binary format, and..."
	
	
	Page 367: Incorrect Explanation For Answer
	------------------------------------------
	
	Page 367, explanation for the first question on page 95:
	
	Change:
	"The only way to get a network ID of 254 is to use the entire octet, in this case
	the third octet."
	
	To:
	"The only way to get a host ID of 254 is to use the entire octet, in this case
	the third octet."
	
	
	Microsoft Press is committed to providing informative and accurate books. All
	comments and corrections listed above are ready for inclusion in future
	printings of this book. If you have a later printing of this book, it may
	already contain most or all of the above corrections.
	
	Additional query words: 1-57231-623-2 TKBOOK
	
	======================================================================
	Keywords          : kbdocfix kbdocerr 
	Technology        : kbMSPressSearch
	Version           : :
	Issue type        : kbinfo
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
