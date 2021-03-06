---
layout: page
title: "Q285672: HOWTO: Create VFP Forms That Remember Size and Position"
permalink: /kb/285/Q285672/
---

## Q285672: HOWTO: Create VFP Forms That Remember Size and Position

{% raw %}

	Article: Q285672
	Product(s): Microsoft FoxPro
	Version(s): 5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): kbCtrl kbDesigner kbOOP kbvfp500 kbvfp600 kbGrpDSFox kbDSupport kbCodeSnippet
	Last Modified: 09-MAR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The size and position of forms that are created with Visual FoxPro (VFP) are not
	automatically saved between instances of the form. However, it is possible to
	build this capability into the forms that you create with VFP.
	
	MORE INFORMATION
	================
	
	The following code uses the Registry object that is defined in the Registry.prg
	file. This program ships with VFP versions 5.0 and 6.0 and is found in the
	Samples\Classes folder. This folder is located under the default HOME() folder
	in VFP 5.0, and is included with the Microsoft Developer Network (MSDN) Help in
	VFP 6.0.
	
	IMPORTANT:You must have access to Registry.prg in order to use this code.
	
	To use this code, follow these steps:
	
	1. Start VFP and create a new form.
	
	2. On the Form menu, click New Property to create a new property. Name the new
	  property oReg. Then create another new property and name it Save_Size_Pos.
	  Change the value of the Save_Size_Pos property to .T., but do not change the
	  value of the oReg property.
	
	3. Paste the following code into the Load event of the form:
	
	  *-----------------------------------
	  * PROCEDURE Load
	  *
	  * AUTHOR:   Trevor Hancock, Microsoft
	  *           (TREVORH@MICROSOFT.COM)
	  * CREATED:  2/6/2001 12:48:04 PM
	  *           for Microsoft Knowledge Base
	  *           article Q285672.
	  * ABSTRACT: The code writes the form size and position
	  *           to the registry in order to retain
	  *           these values between instances.
	  *-----------------------------------
	
	  *!* The code uses an application name as the root entry
	  *!* under HKCU\Software. This could be passed from
	  *!* an application object, but for simplicity it is
	  *!* hard coded here.
	  #DEFINE AppName	[A Fox Test]
	  #DEFINE HKEY_CURRENT_USER	-2147483647
	
	  *!* If you use this form as a base class for all your forms,
	  *!* some (such as dialog boxes) might not need to have their
	  *!* size and position saved. To facilitate this,
	  *!* a Boolean property (Save_Size_Pos) of the form
	  *!* can be set. .T. = Save the size and position.
	  IF THIS.Save_Size_Pos
	  	WITH THIS
	  		LOCAL lnKeyExist, lnTop, lnLeft, lnWidth, lnHeight, lcFormKey
	  		lcFormKey = [SOFTWARE] + [\] + AppName + [\] + .NAME
	
	  		************ START DEV OPTIONAL BLOCK **************
	  		* You could use NEWOBJECT() here in VFP 6.0 instead of
	  		* SET PROCEDURE and CREATEOBJECT():
	  		*
	  		* .oReg = NEWOBJECT([REGISTRY],HOME(2)+ [CLASSES\REGISTRY.PRG])
	  		*
	  		* If you use this form in an .exe file, you should remove
	  		* this code block and include Registry.prg in your project.
	  		*
	  		IF [5] $ VERSION()
	  			SET PROCEDURE TO HOME()+ [\SAMPLES\CLASSES\REGISTRY.PRG] ADDITIVE
	  		ELSE
	  			SET PROCEDURE TO HOME(2)+ [CLASSES\REGISTRY.PRG] ADDITIVE
	  		ENDIF
	  		*
	  		********************* END *********************
	
	  		.oReg = CREATEOBJECT([REGISTRY])
	
	  		*!* Check for the registry key. You will receive a positive 
	                    *!* number if the key is not present.
	  		lnKeyExist = .oReg.OpenKey(lcFormKey, HKEY_CURRENT_USER)
	  		.oReg.CloseKey()
	
	  		IF lnKeyExist > 0 && The values don't exist, so let's make them.
	  			.oReg.OpenKey(lcFormKey,HKEY_CURRENT_USER,.T.)
	  			.oReg.SetRegKey([Top], [0], lcFormKey, HKEY_CURRENT_USER)
	  			.oReg.SetRegKey([Left], [0], lcFormKey, HKEY_CURRENT_USER)
	  			.oReg.SetRegKey([Width], ALLTRIM(STR(.WIDTH)), lcFormKey, HKEY_CURRENT_USER)
	  			.oReg.SetRegKey([Height], ALLTRIM(STR(.HEIGHT)), lcFormKey, HKEY_CURRENT_USER)
	  		ENDIF
	
	  		*!* Read values for the form size and position.
	  		.oReg.GetRegKey([Top], @lnTop, lcFormKey, HKEY_CURRENT_USER)
	  		.oReg.GetRegKey([Left], @lnLeft, lcFormKey, HKEY_CURRENT_USER)
	  		.oReg.GetRegKey([Width], @lnWidth, lcFormKey, HKEY_CURRENT_USER)
	  		.oReg.GetRegKey([Height], @lnHeight, lcFormKey, HKEY_CURRENT_USER)
	  		.oReg.CloseKey()
	
	  		*!* Adjust the size and position of this form.
	  		*!* The registry values are CHARACTER, so we need
	  		*!* to convert them.
	  		.TOP = ROUND(VAL(lnTop),0)
	  		.LEFT = ROUND(VAL(lnLeft),0)
	  		.WIDTH = ROUND(VAL(lnWidth),0)
	  		.HEIGHT = ROUND(VAL(lnHeight),0)
	  	ENDWITH
	  ENDIF
	
	4. Paste the following code into the Destroy event of the form:
	
	  *-----------------------------------
	  * PROCEDURE Destroy
	  * 
	  * AUTHOR:   Trevor Hancock, Microsoft
	  *           (TREVORH@MICROSOFT.COM)
	  * CREATED:  2/6/2001 12:48:04 PM
	  *           for Microsoft Knowledge Base
	  *           article Q285672.
	  * ABSTRACT: The code writes the form size and position
	  *           to the registry in order to retain
	  *           these values between instances. 
	  *-----------------------------------
	
	  *!* The code uses an application name as the root entry
	  *!* under HKCU\Software. This could be passed from
	  *!* an application object, but for simplicity it is
	  *!* hard coded here.
	  #DEFINE AppName	[A Fox Test]
	  #DEFINE HKEY_CURRENT_USER	-2147483647
	
	  *!* If you use this form as a base class for all your forms,
	  *!* some (such as dialog boxes) might not need to have their
	  *!* size and position saved. To facilitate this,
	  *!* a Boolean property (Save_Size_Pos) of the form
	  *!* can be set. .T. = Save the size and position.
	  IF THIS.Save_Size_Pos
	  	WITH THIS
	  		PRIVATE lcFormKey
	  		lcFormKey = [SOFTWARE] + [\] + AppName + [\] + .NAME
	
	  		*!* Write the form size and position to the registry.
	  		*!* We don't check for the keys ( as we did in THIS.LOAD() )
	  		*!* because we know the entries are there ( created in THIS.LOAD() ).
	  		.oReg.SetRegKey([Top], ALLTRIM(STR(.TOP)), lcFormKey, HKEY_CURRENT_USER)
	  		.oReg.SetRegKey([Left], ALLTRIM(STR(.LEFT)), lcFormKey, HKEY_CURRENT_USER)
	  		.oReg.SetRegKey([Width], ALLTRIM(STR(.WIDTH)), lcFormKey, HKEY_CURRENT_USER)
	  		.oReg.SetRegKey([Height], ALLTRIM(STR(.HEIGHT)), lcFormKey, HKEY_CURRENT_USER)
	  	ENDWITH
	  ENDIF
	
	5. Save and then run the form.
	
	6. Move and resize the running form, and then close it.
	
	7. Run the form again.
	
	Each time that you run the form, note that it is the same size and in the same
	position as it was when you last closed it.
	
	Additional query words: SIZE RETAIN POSITION WIDTH HEIGHT FORMS AUTOMATIC
	
	======================================================================
	Keywords          : kbCtrl kbDesigner kbOOP kbvfp500 kbvfp600 kbGrpDSFox kbDSupport kbCodeSnippet 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP600 kbVFP500a
	Version           : :5.0,5.0a,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
