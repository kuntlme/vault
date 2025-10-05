---
tags:
  - fleetingnote
  - atom
  - coding
aliases:
Reference Link: (insert link to book)
Page Number:
Topics:
---

- `VIM`

    - `jk -> exit from insert`
    - `<space> nh -> remove search highlight`
    - `/<search key> -> searching`
    - `:source % -> apply changes`
    - `<space> to -> new tab`
    - `<space> tx -> close current tab`
    - `<space> tn -> go to next tab`
    - `<space> tp -> go to previous tab`
    - `<space> tp -> open current buffer in new tab`
    - `<space> tf -> create a new file`
    - `<space> sv -> vertical split tmux`
    - `<space> sh -> horizontal split tumx`
    - `<space> st -> close current tmux`
    - `<ctrl> h j k l -> navigate`
      \*\*Neo-tree comes with multiple “open” commands:

    * `<space> gd -> go to defination`
        - `<space> ee -> toggle tree`
    * `a <filename> -> create file`
    * `a <foldername>/ -> create folder`

    - `Enter` → open in current window
    - `s` → open in horizontal split
    - `v` → open in vertical split
        - `t` → open in a new tab
		- `Ctrl-o` → jump **back**  
		- `Ctrl-i` → jump **forward**		
        - `<space> ef -> toggle tree on current file`
        - `<space> ee -> collapse tree`
        - `<space> ff -> search find file`
        - `<space> fs -> find string`
        - `<space> fr -> find recent file`
        - `<space> fc -> find string under cursor`
        - `<space> ft -> find todo`
        - `<space> wr -> restore session`
        - `<space> ws -> save session`
        - `r -> for rename`
        - `<space> sn -> minimize the current tab`
        - `Session -> window -> pane`

- `tmux`
  _ `tmux new -s NewSession -> make a new session`
  _ `tmux detach -> exit the session`
  _ `tmux ls -> list of tmux`
  _ `tmux attach -t <session_name> -> open a session`
  _ `ctrl+a s -> switch session & enter to select`
  _ ~~`ctrl+a % -> split pane to current window`~~
  _ `ctrl+a - -> vertical split`
  _ `ctrl+a | -> horizontal`
  _ `ctrl+a hjkl  -> resize pane`
  _ `ctrl+a m -> maximize & toggle`
  _ `ctrl+a c -> new window`
  _ `ctrl+a 0,1,2 -> navigate window by number`
  _ `ctrl+a , type name -> name a window`
  _ `ctrl+a n -> navigate window`
  _ `ctrl+a p -> previous window`
  _ `ctrl+a n -> next window`
  _ `ctrl+a w -> see tree of tmux window & session`
  `copy code`
  _ ` ctrl + a [`
  _ `k to up`
  _ `j to down`
  _ `shift j, k`
  _ `ctrl+u -> up page`
  _ `ctrl+d -> down page`
  _ `ctrl+b -> up full page`
  _ `ctrl+f -> down`
  _ `q+start copy`

- `Vim`

    - `NORMAL INSERT`
    - `$` -> end of the line
    - `0` -> start of the line
    - `^` -> at non blank char
    - `f` -> find forward
    - `t` -> toward
    - `;` -> repeat forward
    - `g` -> repeat backward
    - `W` -> next word
    - `W` -> WORD
    - `b` -> backward word
    - `B` -> WORD backward
    - `e` -> current end to word
    - `E` -> WORD
    - `ge` -> backward end of prev word
    - `gE` -> WORD
    - `}` -> go to next paragraph start mean empty line
    - `{` -> back
    - `gg` -> first line
    - `G` -> last line
    - `relative` `5J, 5K`
    - `%` -> open to & close parenthesis
    - `[` -> prev parenthesis `(,{,`
    - `]` -> next
    - `ctrl+f` -> forward full for screen
    - `ctrl+b` -> backward
    - `ctrl+d` -> half forward
    - `ctrl+u` -> half backward
    - `zz` -> middle
    - `zt` -> top
    - `zb` -> bottom
    - `ctrl+E` -> scroll down
    - `ctrl+y` -> scroll up

- `/` -> `search`
- `n` -> forward search result
- `N` -> backward
- `gg`
    - `9 27`
    - `938`
    - `G 43`
    - `ctrl+O` -> go back to jumplist
    - `ctrl+I` -> forward to
    - `d` -> `d` delete
    - `d$` -> delete to end
    - `u` -> undo
    - `ctrl+R` -> redo
    - `dd` -> delete to whole line
    - `d2W` -> delete 2 Word
    - `d d` -> delete a line
    - `.` -> repeat the same thing
    - `r` -> `r` to replace
    - `x` -> `x` to delete single char
    - `y` -> copy
    - `yy` -> copy whole line
    - `p` -> post
    - `gU` -> uppercase
    - `gu` -> lowercase
    - `U` -> undo
    - `diw` -> delete inside word
    - `dip` -> paragraph
    - `yiw` -> copy
    - `di(` -> delete all everything inside ()
    - `da(` -> with ))
    - `c` -> change
    - `ci`
    - `ca`
    - `:$s/<search>/<replace>/# Content -`

g`

- `:%s`
- `I` -> ask confirmation
- `a` -> append after insert
- `A` -> end of the line insert
- `o` -> open a new line below
- `O` -> open a new line up
