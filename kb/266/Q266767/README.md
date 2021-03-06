---
layout: page
title: "Q266767: HOWTO: Set Which Printer Is the System Default Printer"
permalink: /kb/266/Q266767/
---

## Q266767: HOWTO: Set Which Printer Is the System Default Printer

{% raw %}

	Article: Q266767
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbprint kbAPI kbGDI kbPrinting kbSDKWin32 kbSpooler kbVBp kbVBp400 kbVBp500 kbVBp600 kb
	Last Modified: 04-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 4.0, 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 4.0, 5.0, 6.0 
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows how to programmatically set which printer is the system
	default printer. Not all applications or components can select a specific
	printer to use. This often makes it necessary to change the default printer for
	the system so that the application or component will use the desired printer.
	
	MORE INFORMATION
	================
	
	NOTE: This code changes the default printer for the entire system. So all
	applications that do not specify a printer, even applications that are currently
	running, use this same default. For this reason, you may want to have your code
	remember the previous default and then set it back when your print job is
	finished.
	
	The following code sample provides a means to determine which printers are
	available, and to designate one as the system default printer.
	
	Step-by-Step Example
	--------------------
	
	1. Start a new Standard EXE project in Visual Basic. Form1 is created by
	  default.
	
	2. Add a new module to the project and insert the following code:
	
	  Public Const HWND_BROADCAST = &HFFFF
	  Public Const WM_WININICHANGE = &H1A
	
	  ' constants for DEVMODE structure
	  Public Const CCHDEVICENAME = 32
	  Public Const CCHFORMNAME = 32
	
	  ' constants for DesiredAccess member of PRINTER_DEFAULTS
	  Public Const STANDARD_RIGHTS_REQUIRED = &HF0000
	  Public Const PRINTER_ACCESS_ADMINISTER = &H4
	  Public Const PRINTER_ACCESS_USE = &H8
	  Public Const PRINTER_ALL_ACCESS = (STANDARD_RIGHTS_REQUIRED Or _
	  PRINTER_ACCESS_ADMINISTER Or PRINTER_ACCESS_USE)
	
	  ' constant that goes into PRINTER_INFO_5 Attributes member
	  ' to set it as default
	  Public Const PRINTER_ATTRIBUTE_DEFAULT = 4
	
	  ' Constant for OSVERSIONINFO.dwPlatformId
	  Public Const VER_PLATFORM_WIN32_WINDOWS = 1
	
	  Public Type OSVERSIONINFO
	      dwOSVersionInfoSize As Long
	      dwMajorVersion As Long
	      dwMinorVersion As Long
	      dwBuildNumber As Long
	      dwPlatformId As Long
	      szCSDVersion As String * 128
	  End Type
	
	  Public Type DEVMODE
	       dmDeviceName As String * CCHDEVICENAME
	       dmSpecVersion As Integer
	       dmDriverVersion As Integer
	       dmSize As Integer
	       dmDriverExtra As Integer
	       dmFields As Long
	       dmOrientation As Integer
	       dmPaperSize As Integer
	       dmPaperLength As Integer
	       dmPaperWidth As Integer
	       dmScale As Integer
	       dmCopies As Integer
	       dmDefaultSource As Integer
	       dmPrintQuality As Integer
	       dmColor As Integer
	       dmDuplex As Integer
	       dmYResolution As Integer
	       dmTTOption As Integer
	       dmCollate As Integer
	       dmFormName As String * CCHFORMNAME
	       dmLogPixels As Integer
	       dmBitsPerPel As Long
	       dmPelsWidth As Long
	       dmPelsHeight As Long
	       dmDisplayFlags As Long
	       dmDisplayFrequency As Long
	       dmICMMethod As Long        ' // Windows 95 only
	       dmICMIntent As Long        ' // Windows 95 only
	       dmMediaType As Long        ' // Windows 95 only
	       dmDitherType As Long       ' // Windows 95 only
	       dmReserved1 As Long        ' // Windows 95 only
	       dmReserved2 As Long        ' // Windows 95 only
	  End Type
	
	  Public Type PRINTER_INFO_5
	       pPrinterName As String
	       pPortName As String
	       Attributes As Long
	       DeviceNotSelectedTimeout As Long
	       TransmissionRetryTimeout As Long
	  End Type
	
	  Public Type PRINTER_DEFAULTS
	       pDatatype As Long
	       pDevMode As Long
	       DesiredAccess As Long
	  End Type
	
	  Declare Function GetProfileString Lib "kernel32" _
	  Alias "GetProfileStringA" _
	  (ByVal lpAppName As String, _
	  ByVal lpKeyName As String, _
	  ByVal lpDefault As String, _
	  ByVal lpReturnedString As String, _
	  ByVal nSize As Long) As Long
	
	  Declare Function WriteProfileString Lib "kernel32" _
	  Alias "WriteProfileStringA" _
	  (ByVal lpszSection As String, _
	  ByVal lpszKeyName As String, _
	  ByVal lpszString As String) As Long
	
	  Declare Function SendMessage Lib "user32" _
	  Alias "SendMessageA" _
	  (ByVal hwnd As Long, _
	  ByVal wMsg As Long, _
	  ByVal wParam As Long, _
	  lparam As String) As Long
	
	  Declare Function GetVersionExA Lib "kernel32" _
	  (lpVersionInformation As OSVERSIONINFO) As Integer
	
	  Public Declare Function OpenPrinter Lib "winspool.drv" _
	  Alias "OpenPrinterA" _
	  (ByVal pPrinterName As String, _
	  phPrinter As Long, _
	  pDefault As PRINTER_DEFAULTS) As Long
	
	  Public Declare Function SetPrinter Lib "winspool.drv" _
	  Alias "SetPrinterA" _
	  (ByVal hPrinter As Long, _
	  ByVal Level As Long, _
	  pPrinter As Any, _
	  ByVal Command As Long) As Long
	
	  Public Declare Function GetPrinter Lib "winspool.drv" _
	  Alias "GetPrinterA" _
	  (ByVal hPrinter As Long, _
	  ByVal Level As Long, _
	  pPrinter As Any, _
	  ByVal cbBuf As Long, _
	  pcbNeeded As Long) As Long
	
	  Public Declare Function lstrcpy Lib "kernel32" _
	  Alias "lstrcpyA" _
	  (ByVal lpString1 As String, _
	  ByVal lpString2 As Any) As Long
	
	  Public Declare Function ClosePrinter Lib "winspool.drv" _
	  (ByVal hPrinter As Long) As Long
	
	      Public Sub SelectPrinter(NewPrinter As String)
	          Dim Prt As Printer
	          
	          For Each Prt In Printers
	              If Prt.DeviceName = NewPrinter Then
	                  Set Printer = Prt
	              Exit For
	              End If
	          Next
	      End Sub
	
	3. Place a ListBox and a CommandButton on Form1.
	
	4. Add the following code to the General Declarations section of Form1:
	
	  Option Explicit
	
	  Private Function PtrCtoVbString(Add As Long) As String
	      Dim sTemp As String * 512, x As Long
	
	      x = lstrcpy(sTemp, Add)
	      If (InStr(1, sTemp, Chr(0)) = 0) Then
	           PtrCtoVbString = ""
	      Else
	           PtrCtoVbString = Left(sTemp, InStr(1, sTemp, Chr(0)) - 1)
	      End If
	  End Function
	
	  Private Sub SetDefaultPrinter(ByVal PrinterName As String, _
	      ByVal DriverName As String, ByVal PrinterPort As String)
	      Dim DeviceLine As String
	      Dim r As Long
	      Dim l As Long
	      DeviceLine = PrinterName & "," & DriverName & "," & PrinterPort
	      ' Store the new printer information in the [WINDOWS] section of
	      ' the WIN.INI file for the DEVICE= item
	      r = WriteProfileString("windows", "Device", DeviceLine)
	      ' Cause all applications to reload the INI file:
	      l = SendMessage(HWND_BROADCAST, WM_WININICHANGE, 0, "windows")
	  End Sub
	
	  Private Sub Win95SetDefaultPrinter()
	      Dim Handle As Long          'handle to printer
	      Dim PrinterName As String
	      Dim pd As PRINTER_DEFAULTS
	      Dim x As Long
	      Dim need As Long            ' bytes needed
	      Dim pi5 As PRINTER_INFO_5   ' your PRINTER_INFO structure
	      Dim LastError As Long
	
	      ' determine which printer was selected
	      PrinterName = List1.List(List1.ListIndex)
	      ' none - exit
	      If PrinterName = "" Then
	          Exit Sub
	      End If
	
	      ' set the PRINTER_DEFAULTS members
	      pd.pDatatype = 0&
	      pd.DesiredAccess = PRINTER_ALL_ACCESS Or pd.DesiredAccess
	
	      ' Get a handle to the printer
	      x = OpenPrinter(PrinterName, Handle, pd)
	      ' failed the open
	      If x = False Then
	          'error handler code goes here
	          Exit Sub
	      End If
	
	      ' Make an initial call to GetPrinter, requesting Level 5
	      ' (PRINTER_INFO_5) information, to determine how many bytes
	      ' you need
	      x = GetPrinter(Handle, 5, ByVal 0&, 0, need)
	      ' don't want to check Err.LastDllError here - it's supposed
	      ' to fail
	      ' with a 122 - ERROR_INSUFFICIENT_BUFFER
	      ' redim t as large as you need
	      ReDim t((need \ 4)) As Long
	
	      ' and call GetPrinter for keepers this time
	      x = GetPrinter(Handle, 5, t(0), need, need)
	      ' failed the GetPrinter
	      If x = False Then
	          'error handler code goes here
	          Exit Sub
	      End If
	
	      ' set the members of the pi5 structure for use with SetPrinter.
	      ' PtrCtoVbString copies the memory pointed at by the two string
	      ' pointers contained in the t() array into a Visual Basic string.
	      ' The other three elements are just DWORDS (long integers) and
	      ' don't require any conversion
	      pi5.pPrinterName = PtrCtoVbString(t(0))
	      pi5.pPortName = PtrCtoVbString(t(1))
	      pi5.Attributes = t(2)
	      pi5.DeviceNotSelectedTimeout = t(3)
	      pi5.TransmissionRetryTimeout = t(4)
	
	      ' this is the critical flag that makes it the default printer
	      pi5.Attributes = PRINTER_ATTRIBUTE_DEFAULT
	
	         ' call SetPrinter to set it
	         X = SetPrinter(Handle, 5, pi5, 0)
	
	         If X = False Then   ' SetPrinter failed
	             MsgBox "SetPrinter Failed. Error code: " & Err.LastDllError
	             Exit Sub
	         Else
	             If Printer.DeviceName <> List1.Text Then
	             ' Make sure Printer object is set to the new printer
	                  SelectPrinter (List1.Text)
	             End If
	         End If
	
	      ' and close the handle
	      ClosePrinter (Handle)
	  End Sub
	
	  Private Sub GetDriverAndPort(ByVal Buffer As String, DriverName As _
	      String, PrinterPort As String)
	
	      Dim iDriver As Integer
	      Dim iPort As Integer
	      DriverName = ""
	      PrinterPort = ""
	
	      ' The driver name is first in the string terminated by a comma
	      iDriver = InStr(Buffer, ",")
	      If iDriver > 0 Then
	
	           ' Strip out the driver name
	          DriverName = Left(Buffer, iDriver - 1)
	
	          ' The port name is the second entry after the driver name
	          ' separated by commas.
	          iPort = InStr(iDriver + 1, Buffer, ",")
	
	          If iPort > 0 Then
	              ' Strip out the port name
	              PrinterPort = Mid(Buffer, iDriver + 1, _
	              iPort - iDriver - 1)
	          End If
	      End If
	  End Sub
	
	  Private Sub ParseList(lstCtl As Control, ByVal Buffer As String)
	      Dim i As Integer
	      Dim s As String
	
	      Do
	          i = InStr(Buffer, Chr(0))
	          If i > 0 Then
	              s = Left(Buffer, i - 1)
	              If Len(Trim(s)) Then lstCtl.AddItem s
	              Buffer = Mid(Buffer, i + 1)
	          Else
	              If Len(Trim(Buffer)) Then lstCtl.AddItem Buffer
	              Buffer = ""
	          End If
	      Loop While i > 0
	  End Sub
	
	  Private Sub WinNTSetDefaultPrinter()
	      Dim Buffer As String
	      Dim DeviceName As String
	      Dim DriverName As String
	      Dim PrinterPort As String
	      Dim PrinterName As String
	      Dim r As Long
	      If List1.ListIndex > -1 Then
	          ' Get the printer information for the currently selected
	          ' printer in the list. The information is taken from the
	          ' WIN.INI file.
	          Buffer = Space(1024)
	          PrinterName = List1.Text
	          r = GetProfileString("PrinterPorts", PrinterName, "", _
	              Buffer, Len(Buffer))
	
	          ' Parse the driver name and port name out of the buffer
	          GetDriverAndPort Buffer, DriverName, PrinterPort
	
	             If DriverName <> "" And PrinterPort <> "" Then
	                 SetDefaultPrinter List1.Text, DriverName, PrinterPort
	                 If Printer.DeviceName <> List1.Text Then
	                 ' Make sure Printer object is set to the new printer
	                    SelectPrinter (List1.Text)
	                 End If
	             End If
	  End Sub
	
	  Private Sub Command1_Click()
	      Dim osinfo As OSVERSIONINFO
	      Dim retvalue As Integer
	
	      osinfo.dwOSVersionInfoSize = 148
	      osinfo.szCSDVersion = Space$(128)
	      retvalue = GetVersionExA(osinfo)
	
	      If osinfo.dwPlatformId = VER_PLATFORM_WIN32_WINDOWS Then
	          Call Win95SetDefaultPrinter
	      Else
	      ' This assumes that future versions of Windows use the NT method
	          Call WinNTSetDefaultPrinter
	      End If
	  End Sub
	
	  Private Sub Form_Load()
	      Dim r As Long
	      Dim Buffer As String
	
	      ' Get the list of available printers from WIN.INI
	      Buffer = Space(8192)
	      r = GetProfileString("PrinterPorts", vbNullString, "", _
	         Buffer, Len(Buffer))
	
	      ' Display the list of printer in the ListBox List1
	      ParseList List1, Buffer
	  End Sub
	
	5. Run the project and note that the preceding code populates a ListBox with all
	  available printers.
	
	6. Select one printer in the list and make it the default by clicking the
	  CommandButton.
	
	7. Confirm that the default printer has changed: On the Start button, select
	  Settings, select Printers, and then check which printer is marked as the
	  default. Alternatively, you can print to the default printer from any
	  application on your system.
	
	REFERENCES
	==========
	
	For additional information, click the article numbers below to view the articles
	in the Microsoft Knowledge Base:
	
	  Q167735 FIX: Setting Printer to Item in the Printers Collection Fails
	
	  Q253612 FIX: Printers Collection May Not Contain All Printers in the Printers
	  Folder
	
	  Q246772 HOWTO: Retrieve and Set the Default Printer in Windows
	
	Additional query words: global
	
	======================================================================
	Keywords          : kbprint kbAPI kbGDI kbPrinting kbSDKWin32 kbSpooler kbVBp kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbDSupport kbCodeSnippet 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600 kbVB400Search kbVB400
	Version           : :4.0,5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
