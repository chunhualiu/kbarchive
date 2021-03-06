---
layout: page
title: "Q194923: HOWTO: Trap Control Characters Using the MSComm Control"
permalink: /kb/194/Q194923/
---

## Q194923: HOWTO: Trap Control Characters Using the MSComm Control

{% raw %}

	Article: Q194923
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbIO kbVBp kbVBp500 kbVBp600 kbGrpDSVB kbCodeSam
	Last Modified: 06-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	It is often necessary to look for and react to special unprintable characters
	when using the MSComm control. These characters can include XOn, XOff, STX, ETX
	and others.
	
	MORE INFORMATION
	================
	
	In order to trap these types of characters, you must look for the ASCII value of
	the character, not the string representation of it. Unprintable characters in
	Visual basic are all represented in the same manner, so there is no way to
	differentiate between them without looking at the ASCII value. This is easily
	accomplished by utilizing the Visual Basic Chr$() function.
	
	The following example assumes that you have a null modem cable attached between
	COM1 and COM2. This is only necessary to for testing. App1 is the COM1
	application, App2 is the COM2 application.
	
	Steps to Create App1
	--------------------
	
	1. Create a new Standard EXE project. Form1 is created by default.
	
	2. Choose Components from the Project menu, check the "Microsoft Comm Control,"
	  and click OK.
	
	3. Add an MSCOMM control to the form.
	
	4. Add two CommandButtons to the form.
	
	5. Add the following code to Form1's code window:
	
	        Const Xon = &H11
	        Const Xoff = &H13
	
	        Private Sub Command1_Click()
	           MSComm1.Output = "123456789" & Chr$(Xoff)
	        End Sub
	
	        Private Sub Command2_Click()
	           MSComm1.Output = "987654321" & Chr$(Xon)
	        End Sub
	
	        Private Sub Form_Load()
	           Form1.Caption = "App1"
	           With MSComm1
	              .Handshaking = 2 - comRTS
	              .RThreshold = 1
	              .RTSEnable = True
	              .Settings = "9600,n,8,1"
	              .SThreshold = 1
	              .PortOpen = True
	           End With
	           Command1.Caption = "&Send Xoff"
	           Command2.Caption = "Send &Xon"
	        End Sub
	
	        Private Sub Form_Unload(Cancel As Integer)
	           MSComm1.PortOpen = False
	        End Sub
	
	Steps to Create App2
	--------------------
	
	1. Start a new instance of Visual Basic.
	
	2. Create a new Standard EXE project. Form1 is created by default.
	
	3. Choose Components from the Project menu, check the "Microsoft Comm Control,"
	  and click OK.
	
	4. Add an MSCOMM control to the form.
	
	5. Add a TextBox to the form. Change the MultiLine property of the TextBox to
	  True. Enlarge the TextBox so it will cover most of the form, as you will be
	  displaying all the received data in it.
	
	6. Add a Label to Form1.
	
	7. Add the following code to Form1's code window:
	
	        Const Xon = &H11
	        Const Xoff = &H13
	
	        Private Sub Form_Load()
	           Form1.Caption = "App2"
	           With MSComm1
	              .CommPort = 2
	              .Handshaking = 2 - comRTS
	              .RThreshold = 1
	              .RTSEnable = True
	              .Settings = "9600,n,8,1"
	              .SThreshold = 1
	              .PortOpen = True
	           End With
	           Text1.Text = ""
	        Label1.Caption = "No input yet"
	        End Sub
	
	        Private Sub Form_Unload(Cancel As Integer)
	           MSComm1.PortOpen = False
	        End Sub
	
	        Private Sub MSComm1_OnComm()
	           Dim InBuff As String
	
	           Select Case MSComm1.CommEvent
	           ' Handle each event or error by placing
	           ' code below each case statement.
	
	           ' This template is found in the Example
	           ' section of the OnComm event help topic
	           ' in VB help.
	
	           ' Errors
	              Case comEventBreak   ' A Break was received.
	              Case comEventCDTO    ' CD (RLSD) Timeout.
	              Case comEventCTSTO   ' CTS Timeout.
	              Case comEventDSRTO   ' DSR Timeout.
	              Case comEventFrame   ' Framing Error
	              Case comEventOverrun ' Data Lost.
	              Case comEventRxOver  ' Receive buffer overflow.
	              Case comEventRxParity   ' Parity Error.
	              Case comEventTxFull  ' Transmit buffer full.
	              Case comEventDCB  ' Unexpected error retrieving DCB]
	
	           ' Events
	              Case comEvCD   ' Change in the CD line.
	              Case comEvCTS  ' Change in the CTS line.
	              Case comEvDSR  ' Change in the DSR line.
	              Case comEvRing ' Change in the Ring Indicator.
	              Case comEvReceive ' Received RThreshold # of chars.
	                 Label1.Caption = "Input"
	                 InBuff = MSComm1.Input
	                 Call ParseChars(InBuff)
	              Case comEvSend ' There are SThreshold number of
	                             ' characters in the transmit
	                             ' buffer.
	              Case comEvEOF  ' An EOF character was found in
	                             ' the input stream.
	           End Select
	
	        End Sub
	
	        Sub HandleInput(InBuff As String)
	           ' This is where you will process your input. This
	           ' includes trapping characters, parsing strings,
	           ' separating data fields, etc. For this case, you
	           ' are simply going to display the data in the text
	           ' box.
	
	           Text1.Text = Text1.Text & InBuff
	        End Sub
	
	        Sub ParseChars(ByVal InString As String)
	           Dim temp As String
	           Dim x As Long
	           Dim OutString as String
	
	           For x = 1 To Len(InString)
	              temp = Mid$(InString, x, 1)
	              If temp = Chr$(Xoff) Then
	                 Label1.ForeColor = vbRed
	                 Label1.Caption = "Xoff received"
	                 temp = ""
	              ElseIf temp = Chr$(Xon) Then
	                 Label1.ForeColor = vbGreen
	                 Label1.Caption = "Xon received"
	                 temp = ""
	              End If
	              OutString = OutString & temp
	              temp = ""
	           Next x
	           Call HandleInput(OutString)
	        End Sub
	
	Steps to Run the Applications
	-----------------------------
	
	1. Press the F5 key or click the run button on each project. You will need to
	  move the apps around so you can see them both running at the same time.
	
	2. Make sure you have a standard null modem cable between COM1 and COM2.
	
	3. Click the CommandButton labeled "Send Xoff" on App1. You should see the
	  string "Xoff received" appear in red in App2's label. The string "123456789"
	  will be added to the TextBox, followed by an unprintable control character.
	
	4. Click the CommandButton labeled "Send Xon" on App1. You should see the string
	  "Xon received" appear in green in App2's label. The string "987654321" will
	  be added to the TextBox, followed by an unprintable control character.
	
	Additional query words: mscomm serial xon xoff
	
	======================================================================
	Keywords          : kbcode kbIO kbVBp kbVBp500 kbVBp600 kbGrpDSVB kbCodeSam 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Version           : :5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
