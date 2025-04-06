---
title: "Helix Keymap"
date: 2025-04-06T13:26:05+08:00
draft: false
tags: ["helix", "learning"]
author: ["rikaaa0928"]
categories : ["editor"]
---

=================================================================
=                        CHAPTER 1 RECAP                        =
=================================================================

 * Use the h,j,k,l keys to move the cursor.

 * Type : to enter Command mode.
   * The q / quit and q! / quit! commands will exit Helix. The
     former fails when there are unsaved changes. The latter
     discards them.
   * The w / write command will save the file.
   * The wq / write-quit command will do both.

 * Type d to delete the character at the cursor.

 * Type i to enter Insert mode and type text. Press Escape to
   return to Normal mode.


=================================================================
=                        CHAPTER 2 RECAP                        =
=================================================================

 * Type a to append to the selection.

 * Type I to enter Insert mode at the first non-whitespace
   character at the start of a line.

 * Type A to enter Insert mode at the end of a line.

 * Use o and O to open lines below and above the cursor respectively.


=================================================================
=                        CHAPTER 3 RECAP                        =
=================================================================

 * Type w to select forward until the next word.
   * Type e to select to the end of the current word.
   * Type b to select backward to the start of the current word.
   * Use uppercase counterparts, W,E,B, to traverse WORDS.

 * Type d to delete the entire selection.
   * Type c to delete the selection and enter Insert mode.

 * Type a number before a motion to repeat it that many times.

 * Type v to enter Select mode, where all motions extend the
   selection.

 * Type x to select the entire current line. Type x again to
   select the next line.

 * Type semicolon ( ; ) to collapse selection.


=================================================================
=                        CHAPTER 4 RECAP                        =
=================================================================

 * Type u to undo. Type U to redo.

 * Type y to yank (copy) text and p to paste.
   * Use Space + y and Space + p to yank / paste on the system
     clipboard.

 * Type / to search forward in file, and ? to search backwards.
   * Use n and N to cycle through search matches.



=================================================================
=                        CHAPTER 5 RECAP                        =
=================================================================

 * Type C to duplicate the cursor to the next suitable line
   and Alt-C for previous suitable line.

 * Type s to select all instances of a regex pattern inside
   the current selection.

 * Type & to align selections.

 * Press Alt-s to split the selection into lines.

 
=================================================================
=                        CHAPTER 6 RECAP                        =
=================================================================

 * Type f / F to extend selection up to & including a character.
   * Type t / T to extend selection until a character.

 * Type r to replace selected characters.

 * Type . to repeat the last insertion.
   * Press Alt-. to repeat the last f / t selection.



=================================================================
=                        CHAPTER 7 RECAP                        =
=================================================================

 * Type R to replace the selection with yanked text.

 * Type J to join lines in selection.

 * Type > and < to indent / unindent lines.

 * Press Ctrl-a to increment the selected number.
   * Press Ctrl-x to decrement the selected number.



=================================================================
=                        CHAPTER 8 RECAP                        =
=================================================================

 * Type " to select a different register.

 * Type Q to start and stop recording a macro to a register,
   the default being @.

 * Type q to replay a macro from @ or the selected register.


=================================================================
=                        CHAPTER 9 RECAP                        =
=================================================================

 * Type * to set the search register to the primary selection.

 * Type n / N in Select mode to add selections on each search
   match.

 * Press Ctrl-s to save position to the jumplist.
   * Press Ctrl-i and Ctrl-o to go forward and backward in the
     jumplist.

 * Type gw to enable 2-character labels, and any 2 characters to
   jump to the corresponding label, or ESC to drop the labels.




