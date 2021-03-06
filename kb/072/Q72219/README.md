---
layout: page
title: "Q72219: INFO: Context-Sensitive Help in a Dialog Box Through F1"
permalink: /kb/072/Q72219/
---

## Q72219: INFO: Context-Sensitive Help in a Dialog Box Through F1

{% raw %}

	Article: Q72219
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): _IK kb16bitonly kbDlg kbSDKPlatform kbGrpDSUser kbUser
	Last Modified: 10-JUN-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In an application developed with Windows version 3.0 and later, to implement the
	ability to request context-sensitive help by pressing the F1 key in a dialog
	box, it is necessary to install a message filter.
	
	This article describes how to install the message filter. In particular, it
	describes code that you can add to the Generic sample application (included with
	the Windows Software Development Kit) to install a message filter that would
	detect F1 keystrokes in the About Generic modal dialog box.
	
	MORE INFORMATION
	================
	
	Detecting F1 Keystrokes in a Dialog Box
	---------------------------------------
	
	Normally, the child control windows in a dialog box do not pass keystroke
	messages on to the dialog box window. To detect F1 keystrokes in a dialog box,
	it is necessary to install a message filter.
	
	Installing a Filter Function
	----------------------------
	
	Page 1-65 of the "Microsoft Windows Software Development Kit Reference, Volume 1"
	for version 3.0 of the Windows SDK and page 70 of "Programmer's Reference,
	Volume 1, Overview" for version 3.1 of the Windows SDK describe the method for
	installing a filter function for Windows.
	
	Sample Code
	-----------
	
	Perform the following six steps to add code to the Generic sample application to
	provide context-sensitive help in the About Generic modal dialog box:
	
	1. Define a private message that the filter function can post to the
	  application. For example:
	
	     #define PM_CALLHELP  WM_USER+1000
	                                    // wParam and lParam can be used to
	                                    // pass context information
	
	2. Define global variables:
	
	     FARPROC lpfnFilterProc;        // Our filter function
	        HHOOK hHook;                   // hook handle
	
	3. Add a filter function to the C-language source file. For example:
	
	     /*--------------------------    FilterFunc -------------------------*/ 
	     // 
	     //   PARAMETERS:
	     // 
	     //      nCode : Specifies the type of message being processed. It will
	     //              be either MSGF_DIALOGBOX, MSGF_MENU, or less than 0.
	     // 
	     //      wParam: specifies a NULL value
	     // 
	     //      lParam: a FAR pointer to a MSG structure
	     // 
	     // 
	     //   GLOBAL VARIABLES USED:
	     // 
	     //      hHook
	     // 
	     // 
	     //   NOTES:
	     // 
	     //     If (nCode < 0), return CallNextHookEx IMMEDIATELY.
	     // 
	     //     If (MSGF_DIALOGBOX==nCode), set the local variable ptrMsg to
	     //     point to the message structure. If this message is an F1
	     //     keystroke, ptrMsg->hwnd will contain the HWND for the dialog
	     //     control that the user wants help information on. Post a private
	     //     message to the application, then return 1L to indicate that
	     //     this message was handled.
	     // 
	     //     When the application receives the private message, it can call
	     //     WinHelp. WinHelp must NOT be called directly from the
	     //     FilterFunc() routine.
	     // 
	     //     In this example, post a private PM_CALLHELP message to the
	     //     dialog box. wParam and lParam can be used to pass context
	     //     information.
	     // 
	     //     If the message is not an F1 keystroke, or if nCode is
	     //     MSGF_MENU, we return 0L to indicate that we did not process
	     //     this message.
	     // 
	     // 
	
	     DWORD CALLBACK FilterFunc(nCode, wParam, lParam)
	     int   nCode;
	     WORD  wParam;
	     DWORD lParam;
	     {
	        MSG FAR * ptrMsg;
	
	        if (nCode >= 0)                         // MUST return CallNextHookEx
	        {
	           if (MSGF_DIALOGBOX == nCode)
	           {
	              ptrMsg = (MSG FAR *)lParam;
	
	              if ((WM_KEYDOWN == ptrMsg->message)
	                     && (VK_F1 == ptrMsg->wParam))
	              {
	                 // Use PostMessage here to post an application-defined
	                 // message to the application. Here is one possible call:
	                 PostMessage(GetParent(ptrMsg->hwnd),
	                                        PM_CALLHELP, ptrMsg->hwnd, 0L);
	                 return 1L;                       // Handled it
	              }
	           }
	        }
	        return CallNextHookEx(hHook, nCode, wParam, lParam);
	     }
	     /*--------------------- end FilterFunc  ----------------------------*/ 
	
	4. Export the filter function in the module definition file.
	
	5. Before calling DialogBox(), set the hook. After DialogBox() returns, unhook
	  the hook. For example, the About Generic dialog box could be called as
	  follows:
	
	     case IDM_ABOUT:
	       lpProcAbout    = MakeProcInstance(About, hInst);
	       lpfnFilterProc = MakeProcInstance(FilterFunc, hInst);
	       hHook    = SetWindowsHookEx(WH_MSGFILTER,
	                                         lpfnFilterProc,
	                                         hInst,
	                                         NULL);
	
	       DialogBox(hInst, "AboutBox", hWnd, lpProcAbout);
	
	       UnhookWindowsHookEx(hHook);
	       FreeProcInstance(lpfnFilterProc);
	       FreeProcInstance(lpProcAbout);
	
	       break;
	
	6. Make the application respond to the private message by calling WinHelp.
	
	REFERENCES
	==========
	
	
	
	Additional query words:
	
	======================================================================
	Keywords          : _IK kb16bitonly kbDlg kbSDKPlatform kbGrpDSUser kbUser 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
