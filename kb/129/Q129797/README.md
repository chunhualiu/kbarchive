---
layout: page
title: "Q129797: HOWTO: Launch a Win32 Application from Visual Basic"
permalink: /kb/129/Q129797/
---

## Q129797: HOWTO: Launch a Win32 Application from Visual Basic

{% raw %}

	Article: Q129797
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbAPI kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbDSupport
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	A Windows application can consist of more than one process, and a process can
	consist of more than one thread. The Microsoft Win32 application program
	interface (API) supports multitasking, which creates the effect of simultaneous
	execution of multiple processes and threads. This article describes processes
	and threads, and explains how to create and use them from Microsoft Visual
	Basic, with a step-by-step example.
	
	MORE INFORMATION
	================
	
	A process is a program that is loaded into memory and prepared for execution.
	Each process has a private virtual address space. A process consists of the
	code, data, and other system resources such as files, pipes, and synchronization
	objects that are accessible to the threads of the process. Each process is
	started with a single thread, but additional independently executing threads can
	be created.
	
	A thread can execute any part of the program's code, including a part executed by
	another thread. Threads are the basic entity to which the operating system
	allocates CPU time. Each thread maintains a set of structures for saving its
	context while waiting to be scheduled for processing time. The context includes
	the thread's set of machine registers, the kernel stack, a thread environment
	block, and a user stack in the address space of the thread's process. All
	threads of a process share the virtual address space and can access the global
	variables and system resources of the process.
	
	A multitasking operating system divides the available CPU time among the threads
	that need it. In Windows, the Win32 API is designed for preemptive multitasking;
	this means that the system allocates small slices of CPU time among the
	competing threads. The currently executing thread is suspended when its time
	slice elapses, allowing another thread to run. When the system switches from one
	thread to another, it saves the context of the suspended thread and restores the
	saved context of the next thread in the queue.
	
	Because each time slice is small (approximately 20 milliseconds), it appears that
	multiple threads are executing at the same time. This is actually the case on
	multiprocessor systems where the executable threads are distributed among the
	available processors. On a single processor system, however, using multiple
	threads does not result in more instructions being executed. In fact, the system
	can slow down if it is forced to keep track of too many threads.
	
	How to Launch Win32 Applications from Visual Basic
	--------------------------------------------------
	
	There are two ways to launch another Win32 application from a Microsoft Visual
	Basic application:
	
	- Use the Visual Basic shell command. This spawns a new process and returns its
	  process ID. However, to be able to do anything useful, a process handle is
	  required, which can be obtained by a subsequent call to the OpenProcess Win32
	  API function.
	
	- Use the CreateProcess Win32 API function that creates both a process object
	  and a main thread object. Both the process and the initial thread are
	  assigned a 32-bit identifier that remains valid until the respective object
	  (process or thread) terminates. The 32-bit identifier can be used to uniquely
	  identify the object within the system. The new process and new thread handles
	  are also created with full access rights. All these four values are returned
	  in the PROCESS_INFORMATION structure that is passed by reference to
	  CreateProcess.
	
	The process handle returned by either of the two methods can then be used with
	other Win32 APIs such as TerminateProcess to manipulate the newly launched
	application.
	
	It is important to understand that at creation time, the system gives each object
	an initial usage count of one. Then, just before CreateProcess returns, the
	function opens both the process and the thread object and places the
	process-relative handles for each in the hProcess and hThread members of the
	PROCESS_INFORMATION structure.
	
	When CreateProcess opens these objects, the usage count for each increments to
	two. This means that before the Windows NT or Windows 2000 Executive can free
	the process object, the process must terminate (decrementing the usage count to
	one) and the parent process must call CloseHandle (decrementing the usage count
	to zero). To free the thread object, the thread must terminate and the parent
	process must close the handle to the thread object.
	
	CAUTION: It is very important to close these handles. Failure to do so can result
	in a system memory leak because some Windows NT or Windows 2000 Executive
	objects are never destroyed.
	
	Similar considerations are required when obtaining a process handle with
	OpenProcess. In this case too, the usage count is incremented by one, and unless
	the handle is closed, the process object will remain in memory even when the
	process itself has terminated.
	
	Step-by-Step Example
	--------------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Copy the following code to the Code window of the Form1 form:
	
	  Option Explicit
	
	        Private Type PROCESS_INFORMATION
	           hProcess As Long
	           hThread As Long
	           dwProcessId As Long
	           dwThreadId As Long
	        End Type
	
	        Private Type STARTUPINFO
	           cb As Long
	           lpReserved As String
	           lpDesktop As String
	           lpTitle As String
	           dwX As Long
	           dwY As Long
	           dwXSize As Long
	           dwYSize As Long
	           dwXCountChars As Long
	           dwYCountChars As Long
	           dwFillAttribute As Long
	           dwFlags As Long
	           wShowWindow As Integer
	           cbReserved2 As Integer
	           lpReserved2 As Long
	           hStdInput As Long
	           hStdOutput As Long
	           hStdError As Long
	        End Type
	
	        Private Declare Function CreateProcess Lib "kernel32" _
	           Alias "CreateProcessA" _
	           (ByVal lpApplicationName As String, _
	           ByVal lpCommandLine As String, _
	           lpProcessAttributes As Any, _
	           lpThreadAttributes As Any, _
	           ByVal bInheritHandles As Long, _
	           ByVal dwCreationFlags As Long, _
	           lpEnvironment As Any, _
	           ByVal lpCurrentDriectory As String, _
	           lpStartupInfo As STARTUPINFO, _
	           lpProcessInformation As PROCESS_INFORMATION) As Long
	
	        Private Declare Function OpenProcess Lib "kernel32.dll" _
	           (ByVal dwAccess As Long, _
	           ByVal fInherit As Integer, _
	           ByVal hObject As Long) As Long
	
	        Private Declare Function TerminateProcess Lib "kernel32" _
	           (ByVal hProcess As Long, _
	           ByVal uExitCode As Long) As Long
	
	        Private Declare Function CloseHandle Lib "kernel32" _
	           (ByVal hObject As Long) As Long
	
	        Const SYNCHRONIZE = 1048576
	        Const NORMAL_PRIORITY_CLASS = &H20&
	
	        Private Sub Form_Click()
	           Dim pInfo As PROCESS_INFORMATION
	           Dim sInfo As STARTUPINFO
	           Dim sNull As String
	           Dim lSuccess As Long
	           Dim lRetValue As Long
	
	           sInfo.cb = Len(sInfo)
	           lSuccess = CreateProcess(sNull, _
	                                   "Calc.exe", _
	                                   ByVal 0&, _
	                                   ByVal 0&, _
	                                   1&, _
	                                   NORMAL_PRIORITY_CLASS, _
	                                   ByVal 0&, _
	                                   sNull, _
	                                   sInfo, _
	                                   pInfo)
	
	           MsgBox "Calculator has been launched!"
	
	           lRetValue = TerminateProcess(pInfo.hProcess, 0&)
	           lRetValue = CloseHandle(pInfo.hThread)
	           lRetValue = CloseHandle(pInfo.hProcess)
	
	           MsgBox "Calculator has terminated!"
	        End Sub
	
	3. On the Run menu, select Start, or press the F5 key to start the program.
	  Click on the Form1 form to launch the Calculator application. A message box
	  appears indicating the application has launched successfully. Click OK to
	  close the message box and the Calculator application. Another message box
	  appears indicating the application has successfully terminated.
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q129796 HOWTO: 32-Bit App Can Determine When a Shelled Process Ends
	
	  Q176391 HOWTO: Programmatically Close a Separate Application
	
	Additional query words:
	
	======================================================================
	Keywords          : kbAPI kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbDSupport 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
