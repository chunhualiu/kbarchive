---
layout: page
title: "Q112339: BUG: Opening More Than 61 Files in a FORTRAN Windows NT App"
permalink: /kb/112/Q112339/
---

## Q112339: BUG: Opening More Than 61 Files in a FORTRAN Windows NT App

{% raw %}

	Article: Q112339
	Product(s): Microsoft Fortran Compiler
	Version(s): 1.0,4.0
	Operating System(s): 
	Keyword(s): kbcode kbFortranPS kbLangFortran
	Last Modified: 05-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Fortran Powerstation 32 for Windows NT, versions 1.0, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A FORTRAN PowerStation application on Windows NT can have only 61 files open at
	a time. Attempting to OPEN the file number 62 will produce the run- time error:
	
	  error F6417: too many open files
	
	Page 806 of the FORTRAN PowerStation "Programmer's Guide" incorrectly states that
	the fix for this problem is to change the FILES= setting in CONFIG.SYS.
	
	CAUSE
	=====
	
	The 64-file limit of the PowerStation for MS-DOS has been carried over to
	Powerstation for Windows NT. Three of these files are reserved for system use,
	leaving 61 files for the program to use.
	
	RESOLUTION
	==========
	
	Use WIN32 application programming interface (API) functions to perform some or
	all of your file I/O.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article. We are researching this problem and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	The following sample keeps 100 files open at the same time:
	
	Sample Code #1
	--------------
	
	  c Compile options needed: none
	  c
	
	        include 'IO.FI'
	        program OPEN_TEST
	        character*9 fname/'FILE.000 '/ 
	        integer*4 j
	        fname(9:9) = CHAR(0)  ! Append null character
	        do j = 1,100
	           write(*,*) fname
	           call open(fname)
	           write(fname(6:8),'(i3.3)') j ! Write file extension
	        enddo
	        end
	
	  c
	
	        subroutine open(name)
	        character*(*) name, buffer*16
	        integer lcreat, handle, len
	        data buffer/'Open many files.'/ 
	
	        handle = lcreat(name, 0)         ! Create a new file
	        len = lwrite(handle, buffer, 16) ! Write to file
	        len = llseek(handle, 0, 0)       ! Seek to the beginning
	        len = lread(handle, buffer, 16)  ! Read data back from file
	        end
	
	The following interface file, IO.FI, is used by the program above:
	
	Sample Code #2
	--------------
	
	  C Open an existing file
	
	        interface to integer function lopen
	       +  [stdcall, alias:'__lopen@8'](filename, mode)
	        character*1 filename[reference] ! null terminated file name
	        integer mode[value] ! 0 = read-only, 1 = write-only
	                            ! 2 = read-write
	        end
	
	  C Create a file (erase the old file if one exists)
	
	        interface to integer function lcreat
	       +  [stdcall, alias:'__lcreat@8'](filename, mode)
	        character*1 filename [reference] ! null terminated file name
	        integer mode[value] ! 0 = read-write, 1 = read-only
	                            ! 2 = hidden, 3 = system
	        end
	  C Close a file (use with files opened by lcreat or lopen)
	
	        interface to integer function lclose
	       +  [stdcall, alias:'__lclose@4'](handle)
	        integer handle[value]
	        end
	  C Move the file pointer to a specific offset in a file
	
	        interface to integer function llseek
	       +  [stdcall, alias:'__llseek@12'](handle,offset,origin)
	        integer handle[value]
	        integer offset[value] ! number of bytes to move pointer
	        integer origin[value] ! 0 = beginning, 1 = current position
	                              ! 2 = end of the file
	        end
	  C Read a specified number of bytes from a file
	
	        interface to integer function lread
	       +  [stdcall, alias:'__lread@12'](handle,buffer,length)
	        integer handle[value]
	        character*1 buffer
	        integer length[value]  ! number of bytes
	        end
	  C Write a specified number of bytes to a file
	
	        interface to integer function lwrite
	       +  [stdcall, alias:'__lwrite@12'](handle,buffer,length)
	        integer handle[value]
	        character*1 buffer
	        integer length[value]
	        end
	
	Additional query words: 1.00 4.00
	
	======================================================================
	Keywords          : kbcode kbFortranPS kbLangFortran 
	Technology        : kbAudDeveloper kbFortranSearch kbZNotKeyword2 kbFORTRANPower32100NT kbFORTRANPower32400NT
	Version           : :1.0,4.0
	
	=============================================================================
	

{% endraw %}
