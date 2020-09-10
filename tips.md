## General Tips ##
```
If VIM freeze of hang because you type Ctrl+S (it enables terminal scroll lock) trying to save file,
use Ctrl+q to make terminal work again. 
```
bellow :term   ---  give a terminal window in vim. Within Terminal-Job mode, pressing Ctrl-W N or Ctrl-\ Ctrl-N switches the mode to Terminal-Normal, which allows the cursor to be moved and commands to be ran similarly to Vim's Normal mode. To switch back to Terminal-Job mode, press i. 

*The way that I get around this is:

*pause Vim with Ctrl + Z,

*play in the terminal,

*then return to exactly where you left with Vim by just typing the command fg.

Use Ctrl-w Ctrl-|h|j|k|l to switch between open windows

```
For typing № operation 
№i Type Esc

```
:help ins-special-keys   get manual about shortcuts in insert mode

To enable change in .vimrc file save it :w and then :so % what is meant source file

scriptname  give all info about plugin loag before vim
```
###Mix###
```
:!<cmd>  Execute shell command <cmd>
C-z      send vim to background (fg brings it to front again)
C-n      Keyword completion
Tab      Keyword completion (SuperTab plugin)
r<c>     Replace char <c>
#r<c>    Replace follow # chars with <c>, : csock, cursor on s, 3re ceeek
4gg2yy    Come to 4 line and copy 2 string
```
  
gg=G  it fixes indentation over all document

### vimgrep and quickfix list ###
built-in grep, vimgrep uses vim's quickfix list. see vimcasts#44 for introduction: http://vimcasts.org/episodes/search-multiple-files-with-vimgrep/
```
:vimgrep /<regex>/g %        Search for <regex> with multiple occasions per line (g) 
                             in current file (%)
:vimgrep /<C-r>// %          On the command line, <C-r>/ (that is: CTRL-R followed by /) 
                             will insert the last search pattern.  
:vimgrep /<a>/g <filelist>   Search in the given files (<filelist>) 
:vimgrep /<a>/g *.cc         Search in all *.cc files current directory
:vimgrep /<a>/g **/*.cc      Search in all *.cc files in every sub-directory (recursively) 
:vimgrep /<a>/g `find . -type f`     
                             Search in all files that are returns by the backtick command.
:vim     short for :vimgrep

:cnext   Jump to next record/match in quickfix list
:cprev   Jump to previous record/match in quickfix list
```
Unimpaired plugin (https://github.com/tpope/vim-unimpaired) provides the following mappings:
```
[q       see :cprev
]q       see :cnext
[Q       see :cfirst
]Q       see :clast
```
see also: http://usevim.com/2012/08/24/vim101-quickfix/ and http://vimdoc.sourceforge.net/htmldoc/quickfix.html

### Recording ###
Vim has 26 registers (a-z), select the one you want to record in, see below. Exit Record mode with ESC
```
q[a-z]   Start recording, everything will be recorded including movement actions.
@[a-z]   Execute the recorded actions.    
```


### Spell checking ###
See vimcast #19 as an introduction: http://vimcasts.org/episodes/spell-checking/

Assuming that you have the following in .vimrc:
```
nnoremap <silent> <leader>s :set spell!<cr>
```

```
<leader>s Toggle Spelling
]s       Next spelling mistake
[s       Previous spelling mistake
z=       Give Suggestions (prepent 1, use first suggestions automatically)
zg       Add misspelled to spellfile
zug      Remove word from spellfile
```
see http://vimdoc.sourceforge.net/htmldoc/spell.html

## Marks ##
Mark a position in a buffer and jump back to it. see also http://vim.wikia.com/wiki/Using_marks 
```
ma       set mark a at current cursor location
'a       jump to line of mark a (first non-blank character in line)
`a       jump to position (line and column) of mark a
d'a      delete from current line to line of mark a
d`a      delete from current cursor position to position of mark a
c'a      change text from current line to line of mark a
y`a      yank text to unnamed buffer from cursor to position of mark a
:marks   list all the current marks
:marks aB list marks a, B
```
(text is copied from link above)


# Misc #

```
ga       Show ASCII of char under cursor
```
## .vimrc ##
```
" EITHER the entire 81st column, full-screen...

highlight ColorColumn ctermbg=magenta

set colorcolumn=81

" OR ELSE just the 81st column of wide lines...

highlight ColorColumn ctermbg=magenta

call matchadd('ColorColumn', '\%81v', 100)


"====[ Swap : and ; to make colon commands easier to type ]======

nnoremap  ;  :

nnoremap  :  ;


" OR ELSE use the filetype mechanism to select automatically...

filetype on
augroup PatchDiffHighlight
    autocmd!
    autocmd FileType  diff   syntax enable
augroup END


" EITHER select by the file-suffix directly...

augroup PatchDiffHighlight
    autocmd!
    autocmd BufEnter  *.patch,*.rej,*.diff   syntax enable
augroup END
```
# Key sequences #
#### Replace a word in a number of occurrences with 'bar'; use word under cursor (`*` or `/foo`) ####
`* cw bar ESC n .` 
```
*     word under cursor 'foo'
cw    change word (enter insert mode)
bar   typed new word 'bar'
ESC   exit insert mode
n     next occurrence
.     repeat previous command 
```

#### Insert 3 times "Help!": `Help! Help! Help! ` ####
`3i Help!_ ESC`

#### Insert previously yanked text in line after current ####
`oESCp` 


#### Comment out selection ####
`C-v <select> # ESC ESC`
```
C-v   Enter VISUAL block mode
<sel> Select lines
#     Comment char for programming language (perl, python, bash, etc)
ESC   Exit
ESC   Completes adding comment char for previous selected block
```

# Abbreviations #
auto correction of frequently misspelled words.

```
:abbr Lunix Linux
:abbr accross across
:abbr hte the
```


# Configuration #
* If you set the **incsearch** option, Vim will show the first match for the pattern, while you are still typing it. This quickly shows a typo in the pattern.
* If you set the __hlsearch__ option, Vim will highlight all matches for the pattern with a yellow background. This gives a quick overview of where the search command will take you. In program code it can show where a variable is used. You don't even have to move the cursor to see the matches.


# NERD-tree #
https://github.com/scrooloose/nerdtree/blob/master/doc/NERD_tree.txt
```
F3       Toogle NERD-Tree visible 
```


# ctrlp.vim #
https://github.com/kien/ctrlp.vim
```
C-p      Open ctrlp window (alternative :CtrlP)
:CtrlP d Open CtrlP with specific d = directory
```

```
C-b      Change mode: mru (most recent used) | buffers | files
```

# Formating #
Use `gq` (see Editing section) for formating lines according to configured line-width. 
For C++ formating using clang-format see https://github.com/rhysd/vim-clang-format



# Links #
## Cheat sheets ##
* http://www.worldtimzone.com/res/vi.html
* http://www.fprintf.net/vimCheatSheet.html
* https://wiki.archlinux.org/index.php/Vim
* http://www.fprintf.net/vimCheatSheet.html
* [Yet Another Vim Cheat Sheet](http://rtorruellas.com/vim-cheat-sheet/)


## Articles ##
* Seven habits of effective text editing: http://www.moolenaar.net/habits.html
* Vim After 11 Years: http://statico.github.com/vim.html
* Coming Home to Vim: http://stevelosh.com/blog/2010/09/coming-home-to-vim 


## tipps and tricks ##
*  [medium.com](https://medium.com/@schtoeffel/you-don-t-need-more-than-one-cursor-in-vim-2c44117d51db/) MultiSelection on vim
* [vimcasts.org](http://vimcasts.org/) Video-casts on vim
* [usevim.com](http://usevim.com/) Plugin introductions and useful tipps
* [vimregex.com](http://vimregex.com/) Infos about vims regex engine 
* Productive vim shortcuts http://stackoverflow.com/questions/1218390/what-is-your-most-productive-shortcut-with-vim 
* 100 Vim commands every programmer should know http://www.catswhocode.com/blog/100-vim-commands-every-programmer-should-know
* [VimGenius](http://vimgenius.com/) Interactive vim lesson, with some muscle learn potential
* [Best of VimTips](http://zzapper.co.uk/vimtips.html) zzapper 15 Years of Vi + 8+ years of Vim and still learning 
* http://rayninfo.co.uk/vimtips.html
* Use ag (silver searcher) as an indexer for Ctrl-P; and py-matcher for ctrl-p matching function: http://blog.patspam.com/2014/super-fast-ctrlp
* [Command-T authors cheatsheet](https://wincent.com/wiki/Vim_cheatsheet)
* https://takac.github.io/2013/01/30/vim-grammar/


## Plugins ##
* NERDTree
* NERDCommenter
* Ctrl-P
* easytags
* unimpard
* supertab
* tagbar
* omnicomplete (C++)

## Themes ##
* zenburn
* tango

## Color column ##
* activate colorcolumn: http://stackoverflow.com/questions/1919028/how-to-show-vertical-line-to-wrap-the-line-in-vim
* set color: http://choorucode.wordpress.com/2011/07/29/vim-set-color-of-colorcolumn/

```
:set colorcolumn=81
highlight ColorColumn ctermbg=8
``
