---
layout: page
title: "Q98754: How to Prevent Recursion Within ON KEY LABEL Routines"
permalink: /kb/098/Q98754/
---

## Q98754: How to Prevent Recursion Within ON KEY LABEL Routines

{% raw %}

	Article: Q98754
	Product(s): Microsoft FoxPro
	Version(s): 2.50 2.50a 3.00 | 1.02 2.00 2.50
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 26-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a 
	- Microsoft FoxPro for MS-DOS, versions 1.02, 2.0, 2.5, 2.5a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If a key that is assigned to an ON KEY LABEL procedure is pressed while that
	same procedure is executing, an undesirable recursive condition will be created.
	If this same key is accidentally held down, the typematic function of MS-DOS
	(the rate at which MS-DOS repeats a character when you hold down a key) may fill
	the keyboard buffer with as many as 31 keystrokes.
	
	After attempting to DO the procedure as many times as possible, the program will
	abort with the message "DO nesting too deep."
	
	RESOLUTION
	==========
	
	To work around this problem, turn off the key trap at the beginning of the
	procedure, then set it back on again as the procedure is exited. The sample
	program below demonstrates this workaround.
	
	MORE INFORMATION
	================
	
	The simplest method of disabling an ON KEY LABEL trap is to assign the asterisk
	(*) to the same key label that originally called the currently executing
	procedure. This assignment should be the very first line of the procedure,
	provided there are no parameters to be passed, in which case it should
	immediately follow the PARAMETERS statement.
	
	After the routine has completed its operation, the key can be reassigned to its
	previous command to DO the procedure. This reassignment should be the last line
	in the procedure before the (implied or written) RETURN statement.
	
	
	     *** XYZ.PRG
	     PUSH KEY CLEAR  && Clears and saves current ON KEY LABEL settings
	     ON KEY LABEL F5 DO abc   && original assignment in main program
	
	     &&
	     && body of main program
	     &&
	
	     * (To run this code as a stand-alone program, place a READ CYCLE
	     * command here).
	
	     * Place the POP KEY command immediately before the RETURN (if one
	     * exists) or the end of the main program.
	     POP KEY  && Restores ON KEY LABEL settings
	
	     PROCEDURE abc
	     ON KEY LABEL F5 *   && reassigns F5 to a comment
	     *... other code
	     WAIT WINDOW "pressing F5 now won't call this procedure again"
	     *... more code
	     ON KEY LABEL F5 DO abc   && reassigns F5 to its original trap
	
	
	NOTE: While this method prevents recursive calls from within a procedure, on some
	very fast machines this method will not prevent the procedure call stack from
	overflowing. The "DO nesting too deep" error cannot be trapped by an ON ERROR
	routine, as the ON ERROR routine must place its call on the same stack.
	
	
	Additional query words: VFoxWin FoxDos FoxWin OKL clear typeahead hotkey hot type ahead tshoot
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250 kbFoxPro250a kbVFP300
	Version           : 2.50 2.50a 3.00 | 1.02 2.00 2.50
	
	=============================================================================
	

{% endraw %}
