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
:2t.     Copy second line
:2,5t.   Copy from second to fifth line
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
Moving by Screens

The following commands are used as a quick way to move within the text without scrolling.

    Ctrl + b – move back one full screen
    Ctrl + f – move forward one full screen
    Ctrl + d – move forward 1/2 a screen
    Ctrl + u – move back 1/2 a screen
    Ctrl + e – move screen down one line (without moving the cursor)
    Ctrl + y – move screen up one line (without moving the cursor)
    Ctrl + o – move backward through the jump history
    Ctrl + i – move forward through the jump history

 

    H – move to the top of the screen (H=high)
    M – move to the middle of the screen (M=middle)
    L – move to the bottom of the screen (L=low)

    zz - Center the screen on the cursor
    zt - Scroll the screen so the cursor is at the top
    zb - Scroll the screen so the cursor is at the bottom
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
    E        jump to end of words (no punctuation)
    W        jump by words (spaces separate words)
    B        jump backward by words (no punctuation)
    #G       goto line #
    #gg      goto line #
    :132     go to line 132
```
### Insert Mode ###
```
Ctrl-h          " delete one character
Ctrl-w          " delete one word
Ctrl-u          " delete entire line
Ctrl-r "        " insert the last yank/delete
Ctrl-r %        " insert file name
Ctrl-r /        " insert last search term
Ctrl-r :        " insert last command line
Ctrl-r =        " evaluates and insert result
Ctrl-x Ctrl-y   " scroll up
Ctrl-x Ctrl-e   " scroll down
Ctrl-x Ctrl-l   " insert a whole line
Ctrl-x Ctrl-n   " insert a text from current file
Ctrl-x Ctrl-i   " insert a text from included files
Ctrl-x Ctrl-f   " insert a file name
Ctrl-x Ctrl-]   " insert from tags (must have tags)
Ctrl-x Ctrl-o   " insert from omnicompletion. Filetype specific.
Ctrl-o          " You'll be in insert-normal sub-mode. You can do one normal mode command. Some things you can do:
Ctrl-o zz       " center window
Ctrl-o H/M/L    " jump to top/middle/bottom window
Ctrl-o 'a       " jump to mark 'a'
Ctrl+d          " un-indent current line
Ctrl+t          " indent current line
CTRL-J          " insert newline (easier than reaching for the return key)
Ctrl+e          " insert the character which is below the cursor
Ctrl+y          " insert the character which is above the cursor
Ctrl+a          " insert again whatever the most-recent inserted text was 


:help insert-index :) https://vimhelp.org/index.txt.html#insert-index 
```

### Search, jump ###
consider consulting `:help [` and `:help g`

```
*        search for word under cursor (forward) and highlight occurrence (see incsearch, hlsearch below). Same Shift + 3
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

### Split ####
```
:sp         horisontal split
:vsp        vertical split
C-ww        Jump to the next window
C-wARROW    Jump to window left/right/top/bottom (arrow keys) to the current
C-w _       To increase a window to its maximum height
C-w |       To increase a window to its maximum width

C-w =       To resize all windows to equal dimensions based on their splits
C-w +       Resizing the height of the current window by a single row
C-w -       Resizing the height of the current window by a single row
C-w >       Resizing the width of the current window by a single column
C-w <       Resizing the width of the current window by a single column

z=          To resize all windows to equal dimensions based on their splits, same as C-w =
z0<CR>      To minimize height of current window
z99<CR>     to maxmize height of current window

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
gt              in Normal mod go netx tab
```

### Buffers ###
```
:bfirst:        change to first buffer
:blast:         change to last buffer
:bnext:         change to next buffer
:bprevious:     change to previous buffer
:bdelete        delete buffer and close window
:bclose         close buffer but no window
:bclose N       close N buffer but no window
NUM Ctrl-6      to go to a particular buffer. Add support for buffer in airline plugin
:b <TAB>        to choose from currently opened buffers.
:ls             list of all buffers
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
