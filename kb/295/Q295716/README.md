---
layout: page
title: "Q295716: Host Integration Server May Hinder SNA 4.0 Administration"
permalink: /kb/295/Q295716/
---

## Q295716: Host Integration Server May Hinder SNA 4.0 Administration

{% raw %}

	Article: Q295716
	Product(s): Microsoft SNA Server
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The SNA sub-domain can no longer be managed by any SNA Server in the sub-domain
	under the following circumstances:
	
	- Host Integration Server 2000 (HIS 2000) has been installed as the primary
	  configuration server in an SNA sub-domain.
	
	- The SNA sub-domain contains a version of an SNA server from earlier than HIS
	  2000.
	
	- HIS 2000 SNA Manager makes and saves changes.
	
	When you try to open the SNA Manager from a version of SNA server that is earlier
	than HIS 2000, the SNA Manager window displays "CONFIG READ FAILED RC=3914", and
	an SNAOLE dialog box appears with the following error message:
	
	  The configuration File has been created by a newer version of SNA Server.
	
	CAUSE
	=====
	
	When you save the configuration with the primary Host Integration Server, the
	SNA Com.cfg file is saved with parameters that the SNA 4.0 servers do not
	recognize. This does not effect SNA connectivity, however, and any changes that
	are made with the Host Integration Server or client do take effect.
	
	RESOLUTION
	==========
	
	Upgrade all SNA Servers in the SNA sub-domain to Host Integration Server.
	
	WORKAROUND
	==========
	
	To work around this problem, follow these steps:
	
	1. Export the SNA Com.cfg file to text by using the Snacfg.dll file from the
	  Host Integration Server. Remove the unrecognized parameters, and import the
	  text file into a new SNA 4.0 Com.cfg file by using the SNA 4.0 version of
	  Snacfg.dll.
	
	2. At the command prompt on the primary Host Integration Server, change
	  directory to where the Com.cfg file is located, and then run the export
	  command as follows:
	
	  snacfg #com.cfg /print filename.txt
	
	For example:
	
	  snacfg #c:\Program Files\sna\system\com.cfg /print > c:\temp\export.txt
	
	3. After you convert the file to text, edit the file with a text editor, and
	  then locate the "PRINTSERVER" section, which resembles the following:
	
	  PRINTSERVER SERVERNAME1 /ADD
	
	  /NOTRANSPARENTEVENT:No
	
	  /FLUSHFINALFF:No
	
	  /PROPORTIONALFONT:No
	
	  /LU3DELAYSTART:No
	
	  /LU3DOALLFF:No
	
	  /LU3NOSPACEAFTERFF:No
	
	  /LU3EMBEDDEDCODES:No
	
	  /LU3ALWAYSDONL:No
	
	  /LU1IGNOREUNDER3F:No
	
	  /LU1FIXEDTABS:No
	
	  /APPCRETRYLIMIT:-1
	
	  /APPCRETRYINTERVAL:10
	
	  PRINTSERVER SERVERNAME2 /ADD
	
	  /NOTRANSPARENTEVENT:No
	
	  /FLUSHFINALFF:No
	
	  /PROPORTIONALFONT:No
	
	  /LU3DELAYSTART:No
	
	  /LU3DOALLFF:No
	
	  /LU3NOSPACEAFTERFF:No
	
	  /LU3EMBEDDEDCODES:No
	
	  /LU3ALWAYSDONL:No
	
	  /LU1IGNOREUNDER3F:No
	
	  /LU1FIXEDTABS:No
	
	  /APPCRETRYLIMIT:-1
	
	  /APPCRETRYINTERVAL:10
	
	4. Remove all text below the PRINTSERVER sections of the text file.
	
	  You must do this because the SNA 4.0 Snacfg cannot process the data from that
	  section, and you will receive a "Bad Option Specified" message during the
	  import process for each line that contains these parameters. After you remove
	  the text, this section of the text file appears similar to the following:
	
	  PRINTSERVER SERVERNAME1 /ADD
	
	  PRINTSERVER SERVERNAME2 /ADD
	
	5. Generate a new Com.cfg file:
	
	  a. Copy the Com.cfg file from the I386\system\config folder on the SNA Server
	     4.0 CD-ROM to a folder on your SNA 4.0 server.
	
	  b. At the command prompt, change directory to where you copied the Com.cfg
	     file.
	
	  c. Run the import command as follows to generate the new Com.cfg file:
	
	  snacfg #com.cfg(copied from CD) @filename.txt /V
	
	For example:
	
	  snacfg #com.cfg @c:\temp\export.txt /V
	
	6. Remove the HIS 2000 Server from the SNA sub-domain, replace the Com.cfg file
	  of an existing SNA Server, and then promote that server to the primary of the
	  sub-domain.
	
	MORE INFORMATION
	================
	
	When you upgrade any SNA sub-domain, update the primary SNA server last,
	regardless of the product versions that are involved.
	
	If you have upgraded the primary server first, you must make all changes to the
	sub-domain from the SNA Manager of the earliest version of SNA Server that is in
	the sub-domain.
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbHostIntegServ2000
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
