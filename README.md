

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

### Simple, Practical, and Common #55b18bbea9c2c30d04000001

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



### One number per line #56fb2e75ccffcc0009026473

<https://www.vimgolf.com/challenges/56fb2e75ccffcc0009026473>

**23 steps**

```
dj:%s/,/\r/g<CR>:g/^$/d<CR>ZZ
```

### I forgot quotes #5462e3f41198b80002512673

<https://www.vimgolf.com/challenges/5462e3f41198b80002512673

**16 steps**

```
qqA"<Esc>bi"<Esc>jq2@qZZ
```

### Words in parens #5192f96ad8df110002000002

<https://www.vimgolf.com/challenges/5192f96ad8df110002000002

**17 steps**

```
qqi(<Esc>ea)<Esc>w@qq@qZZ
```

### Simple text editing with Vim #4d1a34ccfa85f32065000004

<https://www.vimgolf.com/challenges/4d1a34ccfa85f32065000004

**30 steps**

```
4G$ya"jp9GdW5wio<C-N><C-N><C-N> <Esc>/ b<CR>nnDZZ
```

### just the middle #54862fbb3f90ac0002904cf5

<https://www.vimgolf.com/challenges/54862fbb3f90ac0002904cf5

**8 steps**

```
dj4GdGZZ
```

### A HAPPY NEW YEAR 2014 !  (52c3cb0d9b8634000200000e)

<http://www.vimgolf.com/challenges/52c3cb0d9b8634000200000e>

**13 steps**

```
wwd2eiNEW<Esc><C-A>ZZ
```

###  Vice versa - 7383 entries (55bcdc3ef4219f456102374f)

<http://www.vimgolf.com/challenges/55bcdc3ef4219f456102374f>

```
2wd2eflPldt.TkpZZ
```

### Reformat/Refactor a Golfer Class - 5779 entries (4d1a1c36567bac34a9000002)

<http://www.vimgolf.com/challenges/4d1a1c36567bac34a9000002>

### prepend * to every non-blank line - 5685 entries (5e4dfcccaa2db400090b66c3)

<http://www.vimgolf.com/challenges/5e4dfcccaa2db400090b66c3>

```
:%s:^.:*&<CR>ZZ
```

###  Basic renumbering - 5391 entries (54595b13128576000257a3c1)

<http://www.vimgolf.com/challenges/54595b13128576000257a3c1>

```
qqywjPdeh10<C-A>0q4@qZZ
```



### **citizen_hacks_2019_challenge2 #5d74187d98328b0006ba474e **

<http://www.vimgolf.com/challenges/5d74187d98328b0006ba474e>

```
vimgolf put 5d74187d98328b0006ba474e
```

For the Citizen Hacks 2019 Vim competition.

##### Start file

```
citizen hacks
```

##### End file

```
Citizen HACKS
```

**7 steps**

```
~w<C-V>e~ZZ
```

**6 steps (best solution)**

```
~w5~ZZ
```



### **Quote modules (ver.2)**

<http://www.vimgolf.com/challenges/5e3ca51e6ea90a00096b3007>

```
vimgolf put 5e3ca51e6ea90a00096b3007
```

Complete golang import statement.

##### Start file

```
import
    log
    net/http

    graphql github.com/graph-gophers/graphql-go
    github.com/graph-gophers/graphql-go/relay
```

##### End file

```
import (
    "log"
    "net/http"

    graphql "github.com/graph-gophers/graphql-go"
    "github.com/graph-gophers/graphql-go/relay"
)
```

**34 steps**

```
A (<Esc>qqjI"<Esc>A"<Esc>q@qjjhi"<Esc>A"<Esc>@qo)<Esc>d0ZZ
```

**23 steps (best solution)**

```
A (<Esc>qqEA"<C-O>B<C-@>$q3@qo<C-U>)<Esc>ZZ
```

### **Paragraph breaks**

<http://www.vimgolf.com/challenges/57cf3e398c660c1f8f014717>

```
vimgolf put 57cf3e398c660c1f8f014717
```

Swap the blank lines and the aaa lines.

##### Start file

```
aa
a
aaa

aa
a
aaa

aa
a
aaa

aa
a
```

##### End file

```
aa
a

aaa
aa
a

aaa
aa
a

aaa
aa
a
```

**13 steps**

```
qq}JkO<Esc>q2@qZZ
```

**10 steps (best solution)**

```
:g/a/m+<CR>ZZ
```

### **Extract wireshark capture filter**

<http://www.vimgolf.com/challenges/5d6b72521c6d070006bded72>

```
vimgolf put 5d6b72521c6d070006bded72
```

Extract wireshark capture filter from IP plan

##### Start file

```
oam_net               10.81.137.0/29    10.81.137.1-10.81.137.6      10.81.137.6    2300
traffic_net_1         10.81.137.16/28   10.81.137.17-10.81.137.30    10.81.137.30   2301
metallb_default_pool  21.21.0.0/24      21.21.0.1-21.21.0.254        21.21.0.254    -
director_ip           10.81.137.0/29    10.81.137.5-10.81.137.5      10.81.137.6    -
oam_net               10.81.137.8/29    10.81.137.9-10.81.137.14     10.81.137.14   2302
traffic_net_1         10.81.137.32/28   10.81.137.33-10.81.137.46    10.81.137.46   2303
istio_ip_1            10.81.139.1/32    10.81.139.1-10.81.139.1      -              -
```

##### End file

```
net 10.81.137.0/29 or net 10.81.137.16/28 or net 21.21.0.0/24 or net 10.81.137.0/29 or net 10.81.137.8/29 or net 10.81.137.32/28 or net 10.81.139.1/32
```

#### **23 steps (best solution)**

```
qq21snet<Esc>ElDJaor <Esc>lq6@qZZ
```

### **Number Sort**

<http://www.vimgolf.com/challenges/5b0ba8a4dd701305aeb59201>

```
vimgolf put 5b0ba8a4dd701305aeb59201
```

sort the list of newline-separated numbers incrementally. Numbers are in the range 1 to 1000, with 500 missing

##### Start file

```
960
90
196
650
219
422
513
...
```

##### End file

```
1
2
3
4
5
9
10
...
```

**10 steps (recommanded)**

```
:sort n<CR>ZZ
```

**9 steps (best solution)**

```
:sor n<CR>ZZ
```



### **Around the clock**

<http://www.vimgolf.com/challenges/5cf9c4c46db575000607ed25>

```
vimgolf put 5cf9c4c46db575000607ed25
```

You'll want to use 2 special commands to complete this. If you haven't yet, read through 'input.txt', especially :help simple-changes

##### Start file

```
Can you decode my ROTten encrypted message?
uvag: uryc fvzcyr-punatr vf lbhe sevraq!
```

##### End file

```
Can you decode my rotten encrypted message?
hint: HELP SIMPLE-CHANGE is your friend!
```

**13 steps (best solution)**

```
Vu~+g?$W18~ZZ
```

### **Simple format (2)**

<http://www.vimgolf.com/challenges/5bf26adb9a198b0009ce0a87>

```
vimgolf put 5bf26adb9a198b0009ce0a87
```

try again!

##### Start file

```
a==b equal to
a!=b not equal to
a>b greater than
a>=b greater than or equal to
a<b less than
a<=b less than or equal to
```

##### End file

```
        a == b          equal to
        a != b          not equal to
        a >  b          greater than
        a >= b          greater than or equal to
        a <  b          less than
        a <= b          less than or equal to
```

**26 steps**

```
qqa <Esc>e3.6|dwls<Tab><Tab><Esc>>><CR>q5@qZZ
```

**23 steps (best solution)**

```
MEi <Esc><C-E>.*l<C-V>nls<Tab><Tab><Esc>>}pEPZZ
```

### **Todo list specification**

<http://www.vimgolf.com/challenges/595cf3b0e9c7a8083500001b>

```
vimgolf put 595cf3b0e9c7a8083500001b
```

The every item on the todo list must be done today. Modify the list to reflect that.

##### Start file

```
#87 do the laundry
#25 take out the trash
#97 wash the dishes
#19 mow the lawn
#48 walk the dog
#89 water the plants
#11 pick up the living room
#64 clean the bathroom
#58 dust the shelves
```

##### End file

```
#87 do the laundry
 87 needs to be done today
#25 take out the trash
 25 needs to be done today
#97 wash the dishes
 97 needs to be done today
#19 mow the lawn
 19 needs to be done today
#48 walk the dog
 48 needs to be done today
#89 water the plants
 89 needs to be done today
#11 pick up the living room
 11 needs to be done today
#64 clean the bathroom
 64 needs to be done today
#58 dust the shelves
 58 needs to be done today
```

**39 steps (first try)**

```
qqlywo <C-O>pneeds to be done today<Esc><CR>q8@qZZ
```

**37 steps (best solution)**

```
qqo <C-Y><C-Y> needs to be done today<Esc><CR>q8@qZZ
```

### **Subnetting**

<http://www.vimgolf.com/challenges/5aa68c3b81f0830009000005>

```
vimgolf put 5aa68c3b81f0830009000005
```

Split up the IP addresses in the right way.

##### Start file

```
37.192.0.0/13
37.192.0.0/13
37.192.0.0/13
37.192.0.0/13
...
```

##### End file

```
37.192.0.0/18
37.192.64.0/18
37.192.128.0/18
37.192.192.0/18
...
```

**37 steps**

```
jdG$r8qqYp4w64<C-A>q2@qqa3kYGpw<C-A>3@qq6@aZZ
```

**29 steps (best soluiton)**

```
qq$<C-V>}r85w<C-V>jj64g<C-A>25w<C-V>}<C-A>q7@q<C-X>ZZ
```

### **Word frequency alignment**

<http://www.vimgolf.com/challenges/50f3c2d55c891f0002000002>

```
vimgolf put 50f3c2d55c891f0002000002
```

You've got to align the second column, but the spacing is inconvenient and there are nasty tabs in the way. If you're a "real Vim ninja," this could be very quick indeed...

##### Start file

```
     align here
the        56271872
of        33950064
and        29944184
to        25956096
in        17420636
I        11764797
that        11073318
was        10078245
his        8799755
he        8397205
it        8058110
```

##### End file

```
     align here
the  56271872
of   33950064
and  29944184
to   25956096
in   17420636
I    11764797
that 11073318
was  10078245
his  8799755
he   8397205
it   8058110
```

**26 steps**

```
:%s:\t:   <CR><C-O>qq<CR>wd6|@qq@qZZ
```

**17 steps**

```
:%s:\t:   <CR><C-O>qq<CR>wd6|@qq@qZZ
```

**5 steps (best solution)**

```
<C-V>)<ZZ
```

### **Suffix sort**

<http://www.vimgolf.com/challenges/53fdb108658ede0002599a8f>

```
vimgolf put 53fdb108658ede0002599a8f
```

Sort from the end of the line, as if the letters in each line were reversed.

##### Start file

```
adjutants
ametropic
audiobook
blockable
demagogic
embryotic
excusable
garroters
housesits
labellers
opacifier
proofroom
quercetin
rejudging
supremely
```

##### End file

```
demagogic
ametropic
embryotic
blockable
excusable
rejudging
audiobook
proofroom
quercetin
opacifier
labellers
garroters
housesits
adjutants
supremely
```

**33 steps**

```
qq$"ax"Ax......"aP<CR>@qq@q:so<Tab><CR>@qZZ
```

`"ax` 使用a寄存器来x

`"Ax` 使用a寄存器来x，并保留a寄存器结果，将新的x内容加入到a寄存器后

**19 steps (best solution)**

```
qq/<C-P>.<CR>:sor//<CR>q7@qZZ
```

### **RUST Cargo.toml version to last**

<http://www.vimgolf.com/challenges/5fe326eb11ba250006cbf2cd>

```
vimgolf put 5fe326eb11ba250006cbf2cd
```

RUST Cargo.toml version to last. rusty practice on vimgolf

##### Start file

```
[package]
name = "rust-web"
version = "0.1.0"
authors = ["The Rust Developers"]
edition = "2018"

[dependencies]
lazy_static = "1.2.0"
fluent = "0.13"
fluent-bundle = "0.6.0"
fluent-syntax = "0.10.0"
fluent-locale = "0.10.1"
handlebars-fluent = "0.2.0"
rand = "0.8"
regex = "1"
rocket = "0.4.6"
serde = { version = "1.0", features = ["derive"] }
serde_yaml = "0.8.14"
sass-rs = "0.2.1"
reqwest = { version = "0.10.10", features = ["blocking", "json"] }
toml = "0.5"
serde_json = "1.0"
rust_team_data = { git = "https://github.com/rust-lang/team" }
handlebars = "1.1.0"
siphasher = "0.3.3"
percent-encoding = "2.1.0"

[dependencies.rocket_contrib]
version = "0.4"
default-features = false
features = ["handlebars_templates"]
```

##### End file

```
[package]
name = "rust-web"
version = "0.1.0"
authors = ["The Rust Developers"]
edition = "2018"

[dependencies]
lazy_static = "*"
fluent = "*"
fluent-bundle = "*"
fluent-syntax = "*"
fluent-locale = "*"
handlebars-fluent = "*"
rand = "*"
regex = "*"
rocket = "*"
serde = { version = "*", features = ["derive"] }
serde_yaml = "*"
sass-rs = "*"
reqwest = { version = "*", features = ["blocking", "json"] }
toml = "*"
serde_json = "*"
rust_team_data = { git = "https://github.com/rust-lang/team" }
handlebars = "*"
siphasher = "*"
percent-encoding = "*"

[dependencies.rocket_contrib]
version = "*"
default-features = false
features = ["handlebars_templates"]
```

**16 steps (best soluiton)**

```
:7,$norm<C-X>ci"*<CR>ZZ
```

### **Add quotes to ansible playbook**

<http://www.vimgolf.com/challenges/5f0f5fbe280fbf000c233304>

```
vimgolf put 5f0f5fbe280fbf000c233304
```

You created an ansible playbook, but forgot to add quotes. Can you fix it?

##### Start file

```
---
- hosts: all
  vars:
    ssh_state: True
  tasks:
    - name: Manage openssh
      package:
        name: openssh
        state: {{ ssh_state }}
```

##### End file

```
---
- hosts: all
  vars:
    ssh_state: True
  tasks:
    - name: Manage openssh
      package:
        name: openssh
        state: "{{ ssh_state }}"
```

**8 steps (best solution)**

```
GWi"<End><C-@>ZZ
```

`<C-@>` Insert previously inserted text and stop insert. (from :help CTRL-@)

### **ssh config skills**

<http://www.vimgolf.com/challenges/5f7337a3a22d0c0009268605>

```
vimgolf put 5f7337a3a22d0c0009268605
```

Parse output from `kuebctl get no -o wide` into an .ssh/config file!

##### Start file

```
master-0-pccc-269-4                Ready                      master   5d3h   v1.18.2   10.0.10.10    <none>
worker-pool1-07p524t4-pccc-269-4   Ready                      worker   5d2h   v1.18.2   10.0.10.17    <none>
worker-pool1-2l7ogj75-pccc-269-4   Ready                      worker   5d2h   v1.18.2   10.0.10.18    <none>
...
```

##### End file

```
host master
  hostname 10.0.10.10

host 07
  hostname 10.0.10.17

host 2l
  hostname 10.0.10.18
...
```

**55 steps (not best)**

```
<C-V>GIhost <Esc>f-qqc5W<CR>  hostname <Esc>ElC<CR><Esc>qoWd2;ll@q<Esc>dd12@"ddZZ
```

### **Alphabet soup**

<http://www.vimgolf.com/challenges/5ebe8a63d8085e000c2f5bd5>

```
vimgolf put 5ebe8a63d8085e000c2f5bd5
```

Create a column of all alphabet characters organized in a funky way

##### Start file

```
a
```

##### End file

```
abcdefghijklmnopqrstuvwxyz
bcdefghijklmnopqrstuvwxyza
cdefghijklmnopqrstuvwxyzab
defghijklmnopqrstuvwxyzabc
efghijklmnopqrstuvwxyzabcd
fghijklmnopqrstuvwxyzabcde
...
```

**41 steps**

```
abcdefghijklmnopqrstuvwxyz<Esc>qqYpx$pq24@qZZ
```

**26 steps**

```
:h<_<CR>jjYZZVpqqYpx$pq24@qZZ
```

**25 steps (best solution)**

```
25RYpx$p<Esc>:h<_<CR>W+YZQVp@"ZZ
```

### **HS Final exam vimgolf**

<https://www.vimgolf.com/challenges/5fa53808a4d481000c3f114d>

```
vimgolf put 5fa53808a4d481000c3f114d
```

Change the initial file to a single line containing all names comma-separated with numbers inside parentheses.

##### Start file

```
   Hossein 40.32472348
    Miguel 50.31417393123
    Pierre 40.1283712
     Anier 45.213917900
 Giancarlo 57.2137189394
     Karim 34.87621341324
  Victoria 23.1236248821
   Nicolas 37.2163718741
   Parshad 40.1273461284
   Shanaya 60.213764127
    Victor 30.2164781849
    Manuel 50.1246215457
```

##### End file

```
Hossein (40), Miguel (50), Pierre (40), Anier (45), Giancarlo (57), Karim (34), Victoria (23), Nicolas (37), Parshad (40), Shanaya (60), Victor (30), Manuel (50)
```

**27 steps (first try)**

```
d0qqwdwi(), <Esc>bpWDJq11@qhDZZ
```

**21 steps (best soluiton)**

```
qqf.C),<C-D><C-O>B(<Esc>Jq11@qxZZ
```

### **Python dataclasses**

https://www.vimgolf.com/challenges/6013804df3308e0009368f1c

```
vimgolf put 6013804df3308e0009368f1c
```

Simple challenge to extract fields from a Python class

##### Start file

```
from dataclasses import dataclass

@dataclass
class Student:
    student_id: str
    name: str
    age: int 
    score: float

fields = ""
```

##### End file

```
from dataclasses import dataclass

@dataclass
class Student:
    student_id: str
    name: str
    age: int 
    score: float

fields = "student_id,name,age,score"
```

**25 steps**

```
5GqqyeGk$Pa,<Esc><C-O><CR>q3@qj$hxZZ
```

**19 steps (best solution)**

```
Gbas<C-N><C-N>,n<C-P>,a<C-P>,s<C-P><C-P><Esc>ZZ
```

### **xrandr outputs and dashes**

<https://www.vimgolf.com/challenges/5ee9ae243a035f000c6141d7>

```
vimgolf put 5ee9ae243a035f000c6141d7
```

uh oh, different video drivers identify display outputs with more dashes. Quick, need to change this xrandr script!

##### Start file

```
xrandr \
  --output VIRTUAL1 --off \
  --output DP3 --off \
  --output eDP1 --off \
  --output DP1 --off \
  --output DP2 --off \
  --output HDMI3 --off \
  --output HDMI2 --off \
  --output HDMI1 --off \
  --output DP3-1 --off \
  --output DP3-3 --off \
  --output DP3-2 --off \
  --output eDP1 --primary --mode 1920x1080
```

##### End file

```
xrandr \
  --output VIRTUAL-1 --off \
  --output DP-3 --off \
  --output eDP-1 --off \
  --output DP-1 --off \
  --output DP-2 --off \
  --output HDMI-3 --off \
  --output HDMI-2 --off \
  --output HDMI-1 --off \
  --output DP-3-1 --off \
  --output DP-3-3 --off \
  --output DP-3-2 --off \
  --output eDP-1 --primary --mode 1920x1080
```

**16 steps**

```
<CR>qq3ei-<Esc><CR>@qq@qZZ
```

**13 steps (best soluiton)**

```
:%s/\d/-&<CR>ZZ
```

### **Multiline to Single Line** (fucking boring)

<https://www.vimgolf.com/challenges/5f0890dbb409320009a38274>

```
vimgolf put 5f0890dbb409320009a38274
```

Convert a multiline, indented file to a single line with no whitespace

##### Start file

```
api(
    'com.vimgolf.challenge'
)
```

##### End file

```
api('com.vimgolf.challenge')
```

**5 steps (best soluiton)**

```
JxJZZ
```

### **Easy modification of ssh config**

https://www.vimgolf.com/challenges/5f8fd2f33dc797000ce6d784

```
vimgolf put 5f8fd2f33dc797000ce6d784
```

Just add another alias to each worker

##### Start file

```
host master
  hostname 10.0.10.8

host 65
  hostname 10.0.10.17

host ef
  hostname 10.0.10.10

host gp
  hostname 10.0.10.27

host h5
  hostname 10.0.10.13

host sa
  hostname 10.0.10.25

host sv
  hostname 10.0.10.12
```

##### End file

```
host master
  hostname 10.0.10.8

host 65 worker1
  hostname 10.0.10.17

host ef worker2
  hostname 10.0.10.10

host gp worker3
  hostname 10.0.10.27

host h5 worker4
  hostname 10.0.10.13

host sa worker5
  hostname 10.0.10.25

host sv worker6
  hostname 10.0.10.12
```

**24 steps (best solution)**

```
qq3+A w<C-P><Esc><C-A>qAorker1<Esc>5@qZZ
```

**27 steps (recommanded)**

```
3jA worker1<Esc>qqyaw3jp<C-A>q4@qZZ
```

### **Enumerate Bullets**

<https://www.vimgolf.com/challenges/5fbfabbbfdf6c50009749916>

```
vimgolf put 5fbfabbbfdf6c50009749916
```

We will need to refer to the bullet points in our document explicitly later, so we need to assign them some ID's!

##### Start file

```
# This is an enumeration of bullet points!
## Usual placeholders:
- foo
- bar
- baz

- (qux)
- (quux)
## pythonic-placeholders:
- spam
- eggs

## cryptographic placeholders:

- alice
- bob
- eve
- trudy

### Search-related:
- needle
- haystack
```

##### End file

```
# This is an enumeration of bullet points!
## Usual placeholders:
01. foo
02. bar
03. baz

04. (qux)
05. (quux)
## pythonic-placeholders:
06. spam
07. eggs

## cryptographic placeholders:

08. alice
09. bob
10. eve
11. trudy

### Search-related:
12. needle
13. haystack
```

**20 steps (best soluiton)**

```
:%s/^-/10.<CR>VHg<C-A><C-V>G<C-X>ZZ
```



### **Data reformat**

<https://www.vimgolf.com/challenges/5eee3ddb30b4450009b4080a>

```
vimgolf put 5eee3ddb30b4450009b4080a
```

Reformat this copy-paste data! #csv

##### Start file

```
Place
Location
Like VimGolf
Like Supernatural
Date
Rating
Sex
Field type
Format
Size
Latitude
Longitude

Andorra Andorra la Vella Y Y 20200150 B M 2.050 P 50 42.506317 1.521835
Argentina Buenos Aires N Y 20191225 A M 13.020 S 4 -34.603722 -58.381592
Cuba Cayo Coco Y Y 20040512 C F 2.052 G 10 22.509001 -78.406998
Egypt The Pyramids of Giza N N 20101005 A M 13.202 D 4 29.976480 31.131302
France Provins Y Y 19780729 B M 1.052 C 13 48.560149 3.299203
Italy The Colosseum of Rome Y Y 20020922 C F 5.043 L 7 41.890251 12.492373
Haiti Port-au-Prince N N 19990101 A F 6.058 S 4 18.533333 -72.333336
Kenya Mombasa N Y 20000515 C F 2.011 T 60 -4.043740 39.658871
Maldives Athuruga Island N N 20040331 B F 5.060 H 2 3.887260 72.816154
Monaco Monte Carlo Y N 20200431 C M 1.025 S 4 43.740070 7.426644
Namibia Windhoek Public Library N N 20050528 B F 2.079 U 23 -22.563906 17.085548
Panama Panama Canal Y Y 19970814 C M 5.034 F 6 9.080000 -79.680000
Portugal Santa Cruz Y N 20171011 B F 2.077 H 2 32.688656 -16.791765
Russia The Moscow Kremlin N N 20070216 D M 6.041 X 5 55.752121 37.617664
Switzerland Grand Hotel Kempinski N Y 19950830 C M 9.041 K 6 46.210281, 6.151083
Tunisia El Mourouj Y Y 19961124 B F 2.055 L 7 36.713432 10.209552
Ukraine Odesa Y N 20130413 A M 4.064 G 10 46.469391 30.740883
United States Empire State Building N N 19880202 D F 1.044 X 5 40.748817 -73.985428
```

##### End file

```
Place;Location;Like VimGolf;Like Supernatural;Date;Rating;Sex;Field type;Format;Size;Latitude;Longitude
Andorra;Andorra la Vella;Y;Y;20200150;B;M;2.050;P;50;42.506317;1.521835
Argentina;Buenos Aires;N;Y;20191225;A;M;13.020;S;4;-34.603722;-58.381592
Cuba;Cayo Coco;Y;Y;20040512;C;F;2.052;G;10;22.509001;-78.406998
Egypt;The Pyramids of Giza;N;N;20101005;A;M;13.202;D;4;29.976480;31.131302
France;Provins;Y;Y;19780729;B;M;1.052;C;13;48.560149;3.299203
Italy;The Colosseum of Rome;Y;Y;20020922;C;F;5.043;L;7;41.890251;12.492373
Haiti;Port-au-Prince;N;N;19990101;A;F;6.058;S;4;18.533333;-72.333336
Kenya;Mombasa;N;Y;20000515;C;F;2.011;T;60;-4.043740;39.658871
Maldives;Athuruga Island;N;N;20040331;B;F;5.060;H;2;3.887260;72.816154
Monaco;Monte Carlo;Y;N;20200431;C;M;1.025;S;4;43.740070;7.426644
Namibia;Windhoek Public Library;N;N;20050528;B;F;2.079;U;23;-22.563906;17.085548
Panama;Panama Canal;Y;Y;19970814;C;M;5.034;F;6;9.080000;-79.680000
Portugal;Santa Cruz;Y;N;20171011;B;F;2.077;H;2;32.688656;-16.791765
Russia;The Moscow Kremlin;N;N;20070216;D;M;6.041;X;5;55.752121;37.617664
Switzerland;Grand Hotel Kempinski;N;Y;19950830;C;M;9.041;K;6;46.210281,;6.151083
Tunisia;El Mourouj;Y;Y;19961124;B;F;2.055;L;7;36.713432;10.209552
Ukraine;Odesa;Y;N;20130413;A;M;4.064;G;10;46.469391;30.740883
United States;Empire State Building;N;N;19880202;D;F;1.044;X;5;40.748817;-73.985428
```

#### **54 steps (first try)**

```
qqJr;q10@qjddqwWhr;qu0qe@w/[Y|N]<CR>b10@w<CR>@eq@e0wr f r;ZZ
```

 **43 steps **

```
11:s:\n:;<CR>JqwF r;quqe<CR>$10@w0,r;q17@er ,r;ZZ
```

**38 steps (best solution)**

```
<C-V>}I;<Esc>xgvgJC<CR>0,.<Esc>10I$F r;<Esc>dd18@1r ,r;ZZ
```

### **Capitalize the Names**

<https://www.vimgolf.com/challenges/5ed621c31a86b700094a80ec>

```
vimgolf put 5ed621c31a86b700094a80ec
```

I want to capitalize the names in quotes, but just the people's names, not the file names.

##### Start file

```
The first name is "JOHN DOE" and its file is "JOHN_DOE.file"
The second name is "JANE DOE" and its file is "JANE_DOE.file"
The third name is "JAMES TIBERIUS KIRK" and its file is "JAMES_TIBERIUS_KIRK.file"
The fourth name is "SPOCK" and its file is "SPOCK.file"
The fifth name is "JEAN-LUC PICARD" and its file is "JEAN_LUC_PICARD.file"
The sixth name is "EUGENE WESLEY RODDENBERRY" and its file is "EUGENE_WESLEY_RODDENBERRY.file"
The seventh name is "WILLIAM NELSON JOY" and its file is "WILLIAM_NELSON_JOY.file"
The last name is "BRAM MOOLENAAR" ind its file is "BRAM_MOOLENAAR.file"
```

##### End file

```
The first name is "John Doe" and its file is "JOHN_DOE.file"
The second name is "Jane Doe" and its file is "JANE_DOE.file"
The third name is "James Tiberius Kirk" and its file is "JAMES_TIBERIUS_KIRK.file"
The fourth name is "Spock" and its file is "SPOCK.file"
The fifth name is "Jean-Luc Picard" and its file is "JEAN_LUC_PICARD.file"
The sixth name is "Eugene Wesley Roddenberry" and its file is "EUGENE_WESLEY_RODDENBERRY.file"
The seventh name is "William Nelson Joy" and its file is "WILLIAM_NELSON_JOY.file"
The last name is "Bram Moolenaar" ind its file is "BRAM_MOOLENAAR.file"
```

#### **40 steps (first try)**

```
qqveu~bqqwf"w@qw@q0;;b@qb@q<CR>q7@w/sp<CR>@qZZ
```

**25 steps**

```
qqf"v;uwvUw.,;b.b.<CR>q7@qZZ
```

`.` 重复上一次的变换

**21 steps (best solution)**

```
qqvi"uvUf"b.b.+q7@qZZ
```

### **move titles next to url, in quotes**

<https://www.vimgolf.com/challenges/5c52df3ff6983b0006c69e80>

```
vimgolf put 5c52df3ff6983b0006c69e80
```

had trouble with something similar

##### Start file

```
https://www.loremipsumdolor.com/atom.xml
https://www.sitametconsectetur.com/rss.xml
https://www.adipiscingelit.com/rss.xml
https://www.integerlacusenim.com/feed.xml
https://www.efficituraceleifendin.com/atom.xml

Lorem Ipsum Dolor
Sit Amet Consectetur
Adipiscing Elit
Integer Lacus Enim
Efficitur ac Eleifend In
```

##### End file

```
https://www.loremipsumdolor.com/atom.xml "Lorem Ipsum Dolor"
https://www.sitametconsectetur.com/rss.xml "Sit Amet Consectetur"
https://www.adipiscingelit.com/rss.xml "Adipiscing Elit"
https://www.integerlacusenim.com/feed.xml "Integer Lacus Enim"
https://www.efficituraceleifendin.com/atom.xml "Efficitur ac Eleifend In"
```

**19 steps (best soluiton)**

```
qq:m6<CR>Ja"<End><C-@>Hq4@qJZZ
```

