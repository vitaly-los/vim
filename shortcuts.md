## Introduction ##
* C-a == Ctrl-a 
* M-a == Alt-a

## General ##

```
vim .    Get list of file in tree mode (netrw)
v        Enter visual mode for selection of LINES
C-v      Enter visual mode for selection of BLOCKS
y        Yank/copy selected region
yy       Yank/copy entire line
y2y      Yank 2 lines
y3y      Yank 3 lines
"<reg>y  Yank/copy marked region into register <reg> (register from a-z)
c        Cut selection
p        Paste yanked content
"<reg>p  Paste yanked content in register <reg> (from a-z)
P        Paste yanked content BEFORE
u        Undo
C-r      Redo
C-[      == Esc
```
### Editing ###
```
:t.      Dublicate line
C-w      Delete word in insert mode 
C-u      Delete line in insert mode
r-       In Normal mode replace symbol r + [a-z]
x        Delete char UNDER cursor
X        Delete char BEFORE cursor
#x       Delete the next # chars. starting from char under cursor
dw       Delete next word
dW       Delete UP TO the next word
d^       Delete up unto the beginning of the line
d$       Delete until end of the line 
D        See d$, delete until end of the line  
dd       Delete whole line and register it in vim buffer
dib      Delete contents in parenthesis '(' ')' block (e.g. function args)
diB      Delete inner '{' '}' block
daB      Delete a '{' '}' block
das      Delete a senctence
diw      Delete word under cursor
df<c>    Delete until next occurence of <c> (char) found (including <c>) [in single line]
dt<c>    Delete until next occurence of <c> (char) found (without <c>!!!) [in single line]
da'      Delete all in '' on line
da[      Delete all in [] on line
da{      Delete all in {} on line
ciw      Change word under cursor 
ciB      Change inner '{' '}' block
cf<c>    See "df<c>" but change instead of delete
ct<c>    See "dt<c>" but change instead of delete
.        Repeat Last Editing operation
Ctrl+d   Auto indent in Insert mode
Ctrl+t   Auto indent in Insert mode
#J       Merge # number of lines together
```
```
gq       (in visual-mode) format selected text according to line-width
gqq      format current line according to line-width
#gqq     format next #-lines  

w !sudo tee %   if forget sudo when editing
```

```
:s/xxx/yyy/    Replace xxx with yyy at the first occurrence
:s/xxx/yyy/g   Replace xxx with yyy first occurrence, global (whole sentence)
:s/xxx/yyy/gc  Replace xxx with yyy global with confirm
:%s/xxx/yyy/g  Replace xxx with yyy global in the whole file
```
```
u        Convert selection (visual mode) to lowercase
U        Convert selection (visual mode) to uppercase
shift + ~ convert character to uppercase under cursor in ocmmand mode
```
```
:g/^#/d  Delete all lines that begins with #
:g/^$/d  Delete all lines that are empty
```

### Navigation ###
_essential_
```
h        cursor left
j        cursor down
l        cursor right
k        cursor up
```

```
_Screen movement commands_

H        Jump to TOP of screen
M        Jump to MIDDLE of screen
L        Jump to BOTTOM of screen
C-b      Move back one full screen (page up)
C-f      Move forward one full screen (page down)
C-d      Move forward 1/2 screen; half page down
C-u      Move back (up) 1/2 screen; half page up
zz  	  Center the screen on the cursor
zt	    Scroll the screen so the cursor is at the top
zb	    Scroll the screen so the cursor is at the bottom
```

```
w        jump by start of words (punctuation considered words)
e        jump to end of words (punctuation considered words)
b        jump backward by words (punctuation considered words)
0 (zero) start of line
^        first non-blank character of line
$        end of line
G        bottom of file
gg       top of file
```
_good to know_
```
E        jump to end of words (no punctuation)
W        jump by words (spaces separate words)
B        jump backward by words (no punctuation)
#G       goto line #
#gg      goto line #
:132     go to line 132
```

### Search, jump ###
consider consulting `:help [` and `:help g`

```
*        search for word under cursor (forward) and highlight occurrence (see incsearch, hlsearch below)
%        jump from open/close ( / #if / ( / { to corresponding ) / #endif / } 
[{       jump to start of current code block
]}       jump to end of current code block
gd       jump to var declaration (see incsearch, hlsearch below)
f<c>     Find char <c> from current cursor position -- forwards
F<c>     Find char <c> from current cursor position -- backwards
,        Repeat previous f<c> or F<c> in opposite direction
;        Repeat previous f<c> or F<c> in same direction
'.       jump back to last edited line.
g;       jump back to last edited position.
[m       jump to start of funtion body
[i       show first declartion/use of the word under cursor
[I       show all occurrences of word under cursor in current file
[/       cursor to N previous start of a C comment
```

# Files #
```
1 C-g        path of current file
C-G          relatile path of current file
C-r %        In insert mode insert file's name

:bp             Buffer Previous open previous opened file
:b[1-9]         open buffered file

:pwd            Print Working Directory
:ls             list
:e .            list of all files in folder
:so %           source file
```

### Inserting a file ###
```
:r[ead] [name]	     Insert the file [name] below the cursor.

:r[ead] !{cmd}	     Execute {cmd} and insert its standard output below the cursor.
```

### Windows ####
```
:sp         gorisontal split
:vsp        vertical split
C-ww        Jump to the next window
C-wARROW    Jump to window left/right/top/bottom (arrow keys) to the current
C-w _       To increase a window to its maximum height
C-w |       To increase a window to its maximum width

C-w =    To resize all windows to equal dimensions based on their splits
C-w +    Resizing the height of the current window by a single row
C-w -    Resizing the height of the current window by a single row
C-w >    Resizing the width of the current window by a single column
C-w <    Resizing the width of the current window by a single column

:res +5     Resize +5 lines in tab
:res -5      Resize -5 lines in tab

:vertical resize 90   right for NERDTreeToggle
:vertical resize +5
:vertical resize -5
```

### Tabs window ###
```
:tabnew filename   open file in new tab
:tabc              closed opened tab
:tabp              tab previous    
:tabn              tab nexts 
:tabl              tab last
:tabn 2            tab number 

vim -p file1.txt file2.txt      start Vim and open  files in diff tabs
```
### Entering insert mode ###
```
a        Append text after the cursor
A        Append text at the end of the line
i        Insert text before the cursor
I        Insert text before the first non-blank in the line
o        Begin a new line BELOW the cursor and insert text
O        Begin a new line ABOVE the cursor and insert text 
s        Erase the current letter under the cursor, set insert-mode
S        Erase the whole line, set insert-mode
cc       Delete the current line, set insert-mode
cw       Delete word, set insert-mode
ce       Delete to end of the word
```
### Exit ###
```
:q        close
:w        write/saves
:wa[!]    write/save all windows [force]
:wq       write/save and close
ZZ        write/save and close 
:x        save and quit, same as wq
:q!       force close if file has changed and not save changes
```

### Plugins ###

```
m     ON NERDTREE files mod

```
