# VimGolf Solution

<http://www.vimgolf.com/>

My ID: <http://www.vimgolf.com/Jianfen22425058>

vimgolf's vimdc: <http://www.vimgolf.com/about>

```
" http://vimdoc.sourceforge.net/htmldoc/starting.html#vimrc

set nocompatible        " use vim defaults
set scrolloff=3         " keep 3 lines when scrolling
set ai                  " set auto-indenting on for programming

set showcmd             " display incomplete commands
set nobackup            " do not keep a backup file
set number              " show line numbers
set ruler               " show the current row and column

set hlsearch            " highlight searches
set incsearch           " do incremental searching
set showmatch           " jump to matches when entering regexp
set ignorecase          " ignore case when searching
set smartcase           " no ignorecase if Uppercase char present

set visualbell t_vb=    " turn off error beep/flash
set novisualbell        " turn off visual bell

set backspace=indent,eol,start  " make that backspace key work the way it should
set runtimepath=$VIMRUNTIME     " turn off user scripts, https://github.com/igrigorik/vimgolf/issues/129

syntax on               " turn syntax highlighting on by default
filetype on             " detect type of file
filetype indent on      " load indent file for specific file type

set t_RV=               " http://bugs.debian.org/608242, http://groups.google.com/group/vim_dev/browse_thread/thread/9770ea844cec3282
```



## Solutions

### Rural Post #5f1e0217becb80000692b9c4

<http://www.vimgolf.com/challenges/5f1e0217becb80000692b9c4>

##### Start file

```
RD 5 Gore 9775
RD 6 Gore 9776
RD 7 Gore 9777
RD 1 Great Barrier Island 0991
RD 1 Greta Valley 7387
RD 1 Greytown 5794
RD 1 Hamilton 3281
RD 2 Hamilton 3282
```

##### End file

```
9775
9776
9777
0991
7387
5794
3281
3282
```

**9 step (best solution)**

```
/.* <CR>g&ZZ
```

`/.* <CR>` 搜索所有满足`.* ` 正则

`g&` 重复所有的替换

**10 step (recommanded)**

```
:%s/.* <CR>ZZ
```

`%s/` 替换

### Add semicolons #5cf62aa56c09760009d6b2f3

<http://www.vimgolf.com/challenges/5cf62aa56c09760009d6b2f3>

##### Start file

```
 super.onCreate(savedInstanceState)
 setContentView(R.layout.activity_second)
 Intent intent = getIntent()
 String text = intent.getStringExtra("text")

 TextView view = findViewById(R.id.textView2)
 view.setText(text)
```

##### End file

```
 super.onCreate(savedInstanceState);
 setContentView(R.layout.activity_second);
 Intent intent = getIntent();
 String text = intent.getStringExtra("text");

 TextView view = findViewById(R.id.textView2);
 view.setText(text);
```

**16 steps (first try)**

```
qqA;<Esc>j@qq@qkkDZZ
```

**13 steps (second try)**

```
:%s/$/;<CR>kkxZZ
```

**12 steps**

```
:%s/.$/&;<CR>ZZ
```

**10 steps (best solution)**

```
<C-V>G$A;<Esc><C-E>xZZ
```

`<C-E>` 向下滚动一页。因为vimrc中设置了 `set scrolloff=3 " keep 3 lines when scrolling`

### ### Simple, Practical, and Common #55b18bbea9c2c30d04000001

##### Start file

```
*temp var1 0
*temp var2 "hi"
*temp var3 -1
*temp var4 42
*temp var5 "asdf"
*temp var6 0

Simple things we do all the time should be able to be done with very few keystrokes, but sometimes I find something I need to do makes me go, "There MUST be a better way."

This challenge is just a simple movement and entering text at a certain place.
```

##### End file

```
*temp var1 0
*temp var2 "hi"
*temp var3 -1
*temp var4 42
*temp var5 "asdf"
*temp var6 0
*temp var7 11

Simple things we do all the time should be able to be done with very few keystrokes, but sometimes I find something I need to do makes me go, "There MUST be a better way."

New text.

This challenge is just a simple movement and entering text at a certain place.
```

**30 steps (first try)**

```
6Gyypf6DA7 11<Esc>9Go<CR>New text.<Esc>ZZ
```

**28 steps**

```
6GYpf6R7 11<Esc>3joNew text.<CR><Esc>ZZ
```

`R` 进入Replace模式

**26 steps**

```
6GYp<C-A>ws11<Esc>3joNew text.<CR><Esc>ZZ
```

`<C-A>` 将当前/下一个 数字增大1

`<C-X>` 将当前/下一个 数字减少1

**23 steps**

```
GONew t<C-N><C-N>.<CR><Esc>6GYp<C-A>l11<C-A>ZZ
```

`<C-N>` 自动补全

**22 steps (best solution)**

```
#Yp<C-A>l11<C-A>GONew t<C-N><C-N>.<CR><Esc>ZZ
```

`#` to the previous **same** word and `*` to the next same word

### **swap number pairs** #5fa95fbdd285680008e41e4b

<https://www.vimgolf.com/challenges/5fa95fbdd285680008e41e4b>

Swap the numbers in a bunch of 2-element arrays.

##### Start file

```
[2, 1], [5, 4]
[6, 3]
[7, 4]
[8, 2], [12, 11]
```

##### End file

```
[1, 2], [4, 5]
[3, 6]
[4, 7]
[2, 8], [11, 12]
```

**28 steps**

```
qq/[<CR>ldwa <Esc>p%%db%p%%hxq5@qZZ
```

**22 steps (recommanded)**

```
qq/[<CR>ldwlpldt]%pq5@qZZ
```

使用 `/[` 搜索定位到下一个括号

**19 steps**

```
qqWdw%pldwWPWq5@qZZ
```

使用 `W` 定位到下一个括号

**17 steps**

```
qq%X%evp<C-O>PWq5@qZZ
```

使用 `X` 向前删除一个字符

使用 `C-O` 跳到上一个位置

**16 steps (best solution) (too tricky)**

```
axepX%p5e<Esc>u6@.ZZ
```

使用 `@.` 来执行剪切板中的指令

### Box it #5c742a5a50bdf70006d43280

<https://www.vimgolf.com/challenges/5c742a5a50bdf70006d43280>

Create a box around a line.

##### Start file

```
My dream is to be in a box
```

##### End file

```
###############################
# My dream was to be in a box #
###############################
```

**29 steps**

```
i# <Esc>fideiwas<Esc>A #<CR>#<Esc>x31pyykPZZ
```












