# Vim Cheatsheet

>Disclaimer: This cheatsheet is summarized from personal experience and other online tutorials. It should not be considered as an official advice.

## Command Line

```bash
vim -p file1 file2              # open files in tabs
vim +{commanmd1} +{command2}    # open vim and run command (e.g. +PlugInstall +q!)
vimn
```

## Global

```bash
:help keyword # open help for keyword
:o[pen] file  # open file
:saveas file  # save file as
:close        # close current pane
```

## Cursor movement

```bash
h        # move cursor left
j        # move cursor down
k        # move cursor up
l        # move cursor right
H        # move to top of screen
M        # move to middle of screen
L        # move to bottom of screen
w        # jump forwards to the start of a word
W        # jump forwards to the start of a word (words can contain punctuation)
e        # jump forwards to the end of a word
E        # jump forwards to the end of a word (words can contain punctuation)
b        # jump backwards to the start of a word
B        # jump backwards to the start of a word (words can contain punctuation)
0        # jump to the start of the line
^        # jump to the first non-blank character of the line
$        # jump to the end of the line
g_       # jump to the last non-blank character of the line
gg       # go to the first line of the document
G        # go to the last line of the document
5G       # go to line 5
fx       # jump to next occurrence of character x
tx       # jump to before next occurrence of character x
}        # jump to next paragraph (or function/block, when editing code)
{        # jump to previous paragraph (or function/block, when editing code)
zz       # center cursor on screen
^b # move back one full screen
^f # move forward one full screen
^d # move forward 1/2 a screen
^u # move back 1/2 a screen
```

## Insert mode - inserting/appending text

```bash
i           # insert before the cursor
I           # insert at the beginning of the line
a           # insert (append) after the cursor
A           # insert (append) at the end of the line
o           # append (open) a new line below the current line
O           # append (open) a new line above the current line
ea          # insert (append) at the end of the word
Esc         # exit insert mode
^v u{nnnn}  # insert unicode character 
```

## Editing

```bash
r        # replace a single character
J        # join line below to the current one
cc       # change (replace) entire line
cw       # change (replace) to the start of the next word
ce       # change (replace) to the end of the next word
cb       # change (replace) to the start of the previous word
c0       # change (replace) to the start of the line
c$       # change (replace) to the end of the line
s        # delete character and substitute text
S        # delete line and substitute text (same as cc)
xp       # transpose two letters (delete and paste)
.        # repeat last command
u        # undo
{n}u     # undo up to the {n}th change
U        # undo latest changes to single line
^r # redo
```

## Marking text (visual mode)

```bash
v        # start visual mode, mark lines, then do a command (like y-yank)
V        # start linewise visual mode
^V       # start blockwise visual mode
o        # move to other end of marked area
O        # move to other corner of block
aw       # mark a word
ab       # a block with ()
aB       # a block with {}
ib       # inner block with ()
iB       # inner block with {}
Esc      # exit visual mode
^v # start visual block mode
```

## Visual commands

```bash
>       # shift text right
<       # shift text left
y       # yank (copy) marked text
d       # delete marked text
~       # switch case
```

## Cut, copy and paste

```bash
yy       # yank (copy) a line
2yy      # yank (copy) 2 lines
yw       # yank (copy) the characters of the word from the cursor position to the start of the next word
y$       # yank (copy) to end of line
p        # put (paste) the clipboard after cursor
P        # put (paste) before cursor
dd       # delete (cut) a line
2dd      # delete (cut) 2 lines
dw       # delete (cut) the characters of the word from the cursor position to the start of the next word
D        # delete (cut) to the end of the line
d$       # delete (cut) to the end of the line
d^       # delete (cut) to the first non-blank character of the line
d0       # delete (cut) to the begining of the line
x        # delete (cut) character
```

## Search and replace

```bash
/pattern       # search for pattern
?pattern       # search backward for pattern
\vpattern      # 'very magic' pattern: non-alphanumeric characters are interpreted as special regex symbols (no escaping needed)
n              # repeat search in same direction
N              # repeat search in opposite direction
:%s/old/new/g  # replace all old with new throughout file
:%s/old/new/gc # replace all old with new throughout file with confirmations
:noh           # remove highlighting of search matches
```

## Search in multiple files

```bash
:vimgrep /pattern/ {file} # search for pattern in multiple files
:cn                       # jump to the next match
:cp                       # jump to the previous match
:copen                    # open a window containing the list of matches
```

## Exiting

```bash
:w              # write (save) the file, but don't exit
:w !sudo tee %  # write out the current file using sudo
:wq or :x or ZZ # write (save) and quit
:q              # quit (fails if there are unsaved changes)
:q! or ZQ       # quit and throw away unsaved changes
```

## Working with multiple files

```bash
:e[dit] file  # edit a file in a new buffer
:bn[ext]      # go to the next buffer
:bp[rev]      # go to the previous buffer
:bd           # delete a buffer (close a file)
:ls           # list all open buffers
:sp[lit] file # open a file in a new buffer and split window
:vsp[lit] file # open a file in a new buffer and vertically split window
^ws           # split window
^ww           # switch windows
^wq           # quit a window
^wv           # split window vertically
^wh           # move cursor to the left window (vertical split)
^wl           # move cursor to the right window (vertical split)
^wj           # move cursor to the window below (horizontal split)
^wk           # move cursor to the window above (horizontal split)
```

## Windows

```bash
:res[ize] [+-]{n}           # resize window by {n} lines horizontally
:vertical resize [+-]{n}    # resize window by {n} lines vertically
:z{n}                       # set current window height to {n}
^W=                         # make all windows (almost) equally high and wide
^W-                         # decrease current window height by 1
^W+                         # increase current window height by 1
```
## Tabs

```bash
:tabnew or :tabnew file # open a file in a new tab
^wT               # move the current split window into its own tab
gt or :tabnext or :tabn # move to the next tab
gT or :tabprev or :tabp # move to the previous tab
{n}gt                   # move to tab {n}
:tabmove {n}            # move current tab to the {n}th position (indexed from 0)
:tabclose or :tabc      # close the current tab and all its windows
:tabonly or :tabo       # close all tabs except for the current one
:tabdo command          # run the command on all tabs (e.g. :tabdo q - closes all opened tabs)
```
