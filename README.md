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









