# 1.Install VIM

    sudo apt-get install -y vim

# 2.Edit .vimrc

## 2.1 How to install the Awesome version?

The awesome version includes a lot of great plugins, configurations and color schemes that make Vim a lot better. To install it simply do following:

    git clone git://github.com/amix/vimrc.git ~/.vim_runtime
    sh ~/.vim_runtime/install_awesome_vimrc.sh

## 2.2 How to update to latest version?

Simply just do a git rebase!

    cd ~/.vim_runtime
    git pull --rebase

## 2.3 Includes

### Included Plugins

I recommend reading the docs of these plugins to understand them better. Each of them provide a much better Vim experience!

* pathogen.vim: Manages the runtime path of the plugins
* YankRing: Maintains a history of previous yanks, changes and deletes
* snipMate.vim: snipMate.vim aims to be a concise vim script that implements some of TextMate's snippets features in Vim
* bufexplorer.zip: Buffer Explorer / Browser. This plugin can be opened with <leader+o>
* NERD Tree: A tree explorer plugin for vim
* ack.vim: Vim plugin for the Perl module / CLI script 'ack'
* ctrlp.vim: Fuzzy file, buffer, mru and tag finder. In my config it's mapped to <Ctrl+F>, because <Ctrl+P> is used by YankRing
* mru.vim: Plugin to manage Most Recently Used (MRU) files. Includes my own fork which adds syntax highlighting to MRU. This plugin can be opened with <leader+f>
* open_file_under_cursor.vim: Open file under cursor when pressing gf
* zencoding: Expanding abbreviation like zen-coding, very useful for editing XML, HTML.
* vim-indent-object: Defines a new text object representing lines of code at the same indent level. Useful for python/vim scripts
* taglist.vim: Source code browser (supports C/C++, java, perl, python, tcl, sql, php, etc)
* vim-multiple-cursors: Sublime Text style multiple selections for Vim, CTRL+N is remapped to CTRL+S (due to YankRing)
* vim-expand-region: Allows you to visually select increasingly larger regions of text using the same key combination.
* vim-airline: Lean & mean status/tabline for vim that's light as air (replacing powerline)
* vim-fugitive: A Git wrapper so awesome, it should be illegal
* goyo.vim and vim-zenroom2: Remove all clutter and focus only on the essential. Similar to iA Writer or Write Room Read more here
* vim-commentary: Comment stuff out. Use gcc to comment out a line (takes a count), gc to comment out the target of a motion. gcu uncomments a set of adjacent commented lines.
* syntastic: Syntax checking hacks for vim

### Included color schemes

* peaksea: My favorite!
* vim-colors-solarized
* vim-irblack
* mayansmoke
* vim-pyte

### Included modes

* vim-coffee-script
* vim-less
* vim-bundle-mako
* vim-markdown
* nginx.vim: Highlights configuration files for nginx
* vim-golang



# 4. Use VIM

    vi有3个模式：插入模式、命令模式、低行模式。

    插入模式：在此模式下可以输入字符，按ESC将回到命令模式。
    命令模式：可以移动光标、删除字符等。
    低行模式：可以保存文件、退出vi、设置vi、查找等功能(低行模式也可以看作是命令模式里的)。

    一、打开文件、保存、关闭文件(vi命令模式下使用)
    vi filename       //打开filename文件
    :w       //保存文件
    :w vpser.net //保存至vpser.net文件
    :q          //退出编辑器，如果文件已修改请使用下面的命令
    :q!        //退出编辑器，且不保存
    :wq         //退出编辑器，且保存文件

    二、插入文本或行(vi命令模式下使用，执行下面命令后将进入插入模式，按ESC键可退出插入模式)
    a      //在当前光标位置的右边添加文本
    i       //在当前光标位置的左边添加文本
    A     //在当前行的末尾位置添加文本
    I      //在当前行的开始处添加文本(非空字符的行首)
    O     //在当前行的上面新建一行
    o     //在当前行的下面新建一行
    R    //替换(覆盖)当前光标位置及后面的若干文本
    J    //合并光标所在行及下一行为一行(依然在命令模式)

    三、移动光标(vi命令模式下使用)

    1、使用上下左右方向键

    2、命令模式下：h 向左、j 向下 、k 向上、l 向右。
    空格键 向右、Backspace 向左、Enter 移动到下一行首、- 移动到上一行首。

    四、删除、恢复字符或行(vi命令模式下使用)  
    x         //删除当前字符
    nx         //删除从光标开始的n个字符
    dd      //删除当前行
    ndd   //向下删除当前行在内的n行
    u       //撤销上一步操作
    U      //撤销对当前行的所有操作

    五、搜索(vi命令模式下使用)   
    /vpser     //向光标下搜索vpser字符串
    ?vpser     //向光标上搜索vpser字符串
    n           //向下搜索前一个搜素动作
    N         //向上搜索前一个搜索动作

    六、跳至指定行(vi命令模式下使用)    
    n+        //向下跳n行
    n-         //向上跳n行
    nG        //跳到行号为n的行
    G           //跳至文件的底部

    七、设置行号(vi命令模式下使用)
    :set  nu     //显示行号
    :set nonu    //取消显示行号

    八、复制、粘贴(vi命令模式下使用)
    yy    //将当前行复制到缓存区，也可以用 "ayy 复制，"a 为缓冲区，a也可以替换为a到z的任意字母，可以完成多个复制任务。
    nyy   //将当前行向下n行复制到缓冲区，也可以用 "anyy 复制，"a 为缓冲区，a也可以替换为a到z的任意字母，可以完成多个复制任务。
    yw    //复制从光标开始到词尾的字符。
    nyw   //复制从光标开始的n个单词。
    y^      //复制从光标到行首的内容。  VPS侦探
    y$      //复制从光标到行尾的内容。
    p        //粘贴剪切板里的内容在光标后，如果使用了前面的自定义缓冲区，建议使用"ap 进行粘贴。
    P        //粘贴剪切板里的内容在光标前，如果使用了前面的自定义缓冲区，建议使用"aP 进行粘贴。

    九、替换(vi命令模式下使用) 
    :s/old/new      //用new替换行中首次出现的old
    :s/old/new/g         //用new替换行中所有的old
    :n,m s/old/new/g     //用new替换从n到m行里所有的old
    :%s/old/new/g      //用new替换当前文件里所有的old

    十、编辑其他文件
    :e otherfilename    //编辑文件名为otherfilename的文件。

    十一、修改文件格式
    :set fileformat=unix   //将文件修改为unix格式，如win下面的文本文件在linux下会出现^M。

# 5.ctags

sudo apt-get install exuberant-ctags

# 6. use

    一.光标移动

    h 或 向左箭头键(←) 光标向左移动一个字符
    20h或者20(←) 光标向左移动20个字符

    j 或 向下箭头键(↓) 光标向下移动一行
    20j或者20(↓) 光标向下移动20行

    k 或 向上箭头键(↑) 光标向上移动一行
    20k或者20(↑) 光标向上移动20行

    l 或 向右箭头键(→) 光标向右移动一个字符
    20l或者20(→) 光标向右移动20字符

    我们可以根据编辑器右下角的数字来判断,我们要跳转到哪一行，如果想更精确的话，:set nu 设置一下环境变量，让它显示行号是最好的
    Ctrl + f    屏幕『向下』移动一页，相当于 [Page Down]按键 (常用)
    Ctrl + b    屏幕『向上』移动一页，相当于 [Page Up] 按键 (常用)
    Ctrl + d    屏幕『向下』移动半页
    Ctrl + u    屏幕『向上』移动半页
    Ctrl + e    屏幕『向下』移动一行
    Ctrl + y    屏幕『向上』移动一行
    +   光标移动到非空格符的下一列
    -   光标移动到非空格符的上一列
    n<space>    那个 n 表示『数字』，按下数字后再按空格键，光标会向右移动这一行的 n 个字符。例如 20<space> 则光标会向后面移动 20 个字符距离。
    n<Enter>    n 为数字。光标向下移动 n 行(常用)
    0 或功能键[Home]    这是数字『 0 』：移动到这一行的最前面字符处 (常用)
    $ 或功能键[End]     移动到这一行的最后面字符处(常用),这里的$在正则里面表示是结尾的意思,这样理解一下就能记住
    H   光标移动到这个屏幕的最上方那一行的第一个字符,H你就把它记成是header的缩写，这样就好记了
    M   光标移动到这个屏幕的中夬那一行的第一个字符,M你就把它记成middle的缩写
    L   光标移动到这个屏幕的最下方那一行的第一个字符,L你就把它记成last的缩写
    G   移动到这个档案的最后一行(常用)
    nG  n 为数字。移动到这个档案的第 n 行。例如 20G 则会移动到这个档案的第 20 行
    gg  移动到这个档案的第一行，相当于 1G 啊！ (常用)

    二.删除，复制，粘贴，撤销

    x, X    在一行字当中，x 为向后删除一个字符 (相当于 [del] 按键)， X 为向前删除一个字符(相当于 [backspace] 亦即是退格键) (常用)

    nx n 为数字，连续向后删除 n 个字符。举例来说，我要连续删除光标后 10 个字符， 『10x』。
    nX n 为数字，连续删除光标前面的 n 个字符。举例来说，我要连续删除光标前的 10 个字符， 『10X』。

    dd 删除光标所在的那一整行(常用)
    yy 复制光标所在的那一行(常用)

    ndd  n 为数字。删除光标所在行向下 n 行，例如 20dd 则是删除 20 行(常用)
    nyy n 为数字。复制光标所在行向下 n 行，例如 20yy 则是复制 20 行(常用)

    d1G 删除光标所在行到第一行的所有数据
    y1G 复制光标所在行到第一行的所有数据

    dG 删除光标所在行到最后一行的所有数据
    yG 复制光标所在行到最后一行的所有数据

    d$ 删除光标所在处，到该行的最后一个字符
    y$ 复制光标所在的那个字符到该行行尾的所有数据

    d0 那个是数字的 0 ，删除光标所在处，到该行的最前面一个字符
    y0 复制光标所在的那个字符到该行行首的所有数据

    p, P    p将复制的数据，粘贴在光标的下一行，P将复制的数据,粘贴到光标的上一行
    J   将光标所在行不下一行的数据结合成同一行
    c   重复删除多个数据，可以通过上下键来决定删除光标上面的，还是下面的
    u   撤销。(常用)
    Ctrl + r    撤销的撤销。(常用)

    三.区块选择，查找，替换
    区块选择，查找，替换
    v   字符选择，会将光标经过的地方反白选择！
    V   行选择，会将光标经过的行反白选择！
    Ctrl + v    区块选择，可以用长方形的方式选择资料
    y   将反白的地方复制起来
    d   将反白的地方删除掉


