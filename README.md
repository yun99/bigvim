bigvim
======================

### 配置步骤

1. clone到本地任意目录

        git clone https://github.com/ruanyl/bigvim.git

2. 安装依赖包

        sudo apt-get install ctags
        sudo apt-get install python-pip
        sudo apt-get install build-essential cmake python-dev  #编译YCM自动补全插件依赖
        brew install ctags     (mac用户)

3. 安装Nodejs
        nodejs.org

4. 安装插件

        cd bigvim/

        sh -x install.sh

        install.sh
        本质上做的事情
        1.将vimrc/vim文件夹软链接到$HOME，编程系统vim配置
        2.git clone安装vundle（clone到bundle目录下）
        3.通过vundle安装其他所有插件（相当于进入vimrc, 命令行执行:BundleInstall）,从github全部搞到本地
        4.安装必须的nodejs包

5. 可能遇到的问题:

   * 相对行号

   vimrc中配置,如果不习惯,可以去掉,[相关参考](http://jeffkreeftmeijer.com/2012/relative-line-numbers-in-vim-for-super-fast-movement/)

   * 配置主题

   到vimrc中修改colortheme,可以使用molokai(用惯sublimetext2的童鞋很熟悉)

   默认配置的是[solarized dark主题](https://github.com/altercation/vim-colors-solarized)

   想要修改终端配色为solarized可以参考 [这里](https://github.com/sigurdga/gnome-terminal-colors-solarized)

   * Powerline美化字体

   推荐[Monaco for Powerline](https://gist.github.com/ruanyl/ea38de37683951c20bf5/raw/5fa73caa4af86285f11539a6b4b6c26cfca2c04b/Monaco%20for%20Powerline.otf) 或者去[Lokaltog/powerline-fonts](https://github.com/Lokaltog/powerline-fonts) 自行寻找


### 其他

5. 安装/卸载/更新插件：

   可能发现打开vim很慢，可能是插件有点多了，这个配置插件全开

   去掉某些自己用不到的插件: 编辑vimrc，注释掉插件对应Bundle行即可(加一个双引号),保存退出即可

        "Bundle 'scrooloose/syntastic'

   如果想从物理上清除（删除插件文件），注释保存后再次进入vim

   命令行模式，执行:

        :BundleClean

   如果要安装新插件，在vimrc中加入bundle，然后执行

        :BundleInstall

   更新插件

        :BundleUpdate

6. 给mac用户

   安装[homebrew](http://brew.sh/)

   使用brew install vim

7. 冲突和问题排查

   插件很多，并且其默认快捷键或者配置可能发生冲突

   当加入新插件发现有冲突或者展现有问题

   排除法进行排查：注掉所有插件或配置，然后二分法逐一恢复，可以定位到出现问题的插件或配置

-------------

### 截图

solarized主题

![solarized](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/solarized.png) 我的终端颜色显示不对，不过这个色调也很舒服

molokai主题

![molokai](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/molokai.png)

-------------

### 自定义快捷键说明

    F1  关掉，防止跳出帮助
    F2  set nu/nonu
    F3  set list/nolist
    F4  set wrap/nowrap
    F5  set paste/nopaste
    F6  syntax on/off
    空格 /开启查找
    Y   =y$   复制到行尾
    w!!  以sudo的权限保存
    t    新起一行，下面，不进入插入模式
    T    新起一行，上面
    ,sa   全选(select all)
    ctrl + jkhl 进行上下左右窗口跳转,不需要ctrl+w+jkhl

    ,y 展示历史剪贴板
    ,yc 清空
    yy/dd -> p -> ctrl+p可以替换非最近一次剪贴内容

    ,f 开启文件搜索 ctrlp
    ,/ 去除匹配高亮

    当打开多个Buffer时：
    映射：' :b，输入数字，:b3快速切换到第三个Tab
    qq 关闭当前Buffer
    qo 关闭除当前buffer之外的所有buffer
    m 在Buffer之间顺序切换
    M 在Buffer之间逆序切换

--------------------

### 插件及其快捷键说明

##### 插件管理

1. ####[gmarik/vundle](https://github.com/gmarik/vundle)

    必装,用于管理所有插件

    命令行模式下管理命令:

        :BundleInstall     install
        :BundleInstall!    update
        :BundleClean       remove plugin not in list


##### 导航及搜索

1. ####[scrooloose/nerdtree](https://github.com/scrooloose/nerdtree)

   必装,开启目录树导航

            ,e  打开 关闭树形目录结构

            m   根据提示执行新建文件，目录，拷贝等操作

            在nerdtree窗口常用操作：(小写当前，大写root)
            x.......Close the current nodes parent收起当前目录树
            R.......Recursively refresh the current root刷新根目录树
            r.......Recursively refresh the current directory刷新当前目录
            P.......Jump to the root node
            p.......Jump to current nodes parent
            K.......Jump up inside directories at the current tree depth  到同目录第一个节点
            J.......Jump down inside directories at the current tree depth 最后一个节点
            o.......Open files, directories and bookmarks
            i.......Open selected file in a split window上下分屏
            s.......Open selected file in a new vsplit左右分屏
   演示

   ![thenerdtree](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/nerdtree.gif)

2. ####[majutsushi/tagbar](https://github.com/majutsushi/tagbar)

        <F9> 打开

   演示

   ![tagbar](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/tagbar.gif)

3. ####[kien/ctrlp.vim](https://github.com/hdima/python-syntax)

   文件搜索,ack/Command-T需要依赖于外部包,不喜欢有太多依赖的,除非十分强大, 具体 [文档](http://kien.github.io/ctrlp.vim/)

        ,f  默认查找 最近使用的+文件搜索+buffer
        ,m  相当于mru功能，most recently used
        ,b  查找buffer

        ctrl + j/k 进行上下移动 或者小键盘方向键

   演示

   ![ctrlp](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/ctrlp.gif)

4. ####[tacahiroy/ctrlp-funky](https://github.com/tacahiroy/ctrlp-funky)

   CtrlP插件，类似go to definition的功能

        ,fu 打开搜索

   演示

   ![ctrlp-funky](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/ctrlp-funky.gif)

##### 显示增强

    被动技能,无快捷键

1. ####[bling/vim-airline](https://github.com/bling/vim-airline)

   ![vim-airline](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/vim-airline.png)

2. ####[gorodinskiy/vim-coloresque](https://github.com/gorodinskiy/vim-coloresque)

   高亮显示文档中颜色代码

   ![vim-coloresque](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/vim-colorsque.png)

3. ####[bronson/vim-trailing-whitespace](https://github.com/bronson/vim-trailing-whitespace)

   将代码行最后无效的空格标红

        ,空格    去掉当前行末尾空格

4. ####[altercation/vim-colors-solarized](https://github.com/altercation/vim-colors-solarized)

   经典主题, 但是颜色需要终端导入色彩方案，我的颜色显示不对，但是看着还是舒服，就那样了。。

5. ####[tomasr/molokai](https://github.com/tomasr/molokai)

   另外一个经典主题

##### 快速移动

    主动技能,需要快捷键

1. ####[Lokaltog/vim-easymotion](https://github.com/Lokaltog/vim-easymotion)

   跳转到任意位置

        s  查找2个字符，例如想要跳到某个方法，只需输入该方法前2个字符，就能跳转到该位置
        ,, + f  向后查找1个字符
        /  替代vim默认的搜索功能，如果不喜欢可以去除

   ![easy_motion](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/easy-motion.gif)

2. ####[Valloric/MatchTagAlways](https://github.com/Valloric/MatchTagAlways)

   高亮显示匹配的标签

   ![matchtagalways](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/matchtagalways.gif)

3. ####[vim-scripts/matchit.zip](https://github.com/vim-scripts/matchit.zip)

   % 匹配标签，不只是单个的字符，还可以匹配单词，如html标签

##### 快速编辑

1. ###[gcmt/wildfire.vim](https://github.com/gcmt/wildfire.vim)

   快速选取代码块

   ![wildfire](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/wildfire.gif)

2. ###[alvan/vim-closetag]

    自动关闭html, xml标签

    ![closetag](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/CloseTag.gif)

3. ###[drmingdrmer/xptemplate](https://github.com/drmingdrmer/xptemplate)

    代码片段工具
        <C-\> 触发
    ![xptemplate](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/xptemplate.gif)

4. ####[scrooloose/nerdcommenter](https://github.com/scrooloose/nerdcommenter)

        shift+v 选择要注释的行   ->
        ,cc  注释单行或者选中行
        ,cm  多行注释
        ,cu  解开注释
        ,ci  在注释和取消注释之间切换

    ![nerdcomment](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/nerdcomment.gif)

5. ####[tpope/vim-surround](https://github.com/tpope/vim-surround)

   配合vim-repeat进行增强,'.'可以重复命令

        ysiw"
        Hello -> "Hello"
        cs"'
        "Hello world!" -> 'Hello world!'
        ds"
        "Hello world!" -> Hello world!

   ![surround](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/surround.gif)

6. ###[tpope/vim-repeat](https://github.com/tpope/vim-repeat)

    重复命令
        .  重复上一次命令

7. ### [Raimondi/delimitMate](https://github.com/Raimondi/delimitMate)

    自动补全：(), [], {}, <>

8. ###[godlygeek/tabular](https://github.com/godlygeek/tabular)

    代码按=或者: 对齐
        ,a=   按等号对齐
        ,a:   安冒号对齐

    ![tabular](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/tabular.gif)

9. ###[terryma/vim-multiple-cursors](https://github.com/terryma/vim-multiple-cursors)

    多光标操作
        ,n  开始选择
        ,x  跳过当前
        ,p  返回选择

    ![multicursor](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/multicursor.gif)

10. ###[mattn/emmet-vim](https://github.com/mattn/emmet-vim)

    快速书写html

    ![emmet](https://raw.githubusercontent.com/ruanyl/ruanyl.github.io/master/images/emmet.gif)

> 自动补全

1. ###[davidhalter/jedi-vim](https://github.com/davidhalter/jedi-vim)

   Python 自动补全以及快速跳转，详情请见其Github主页

2. ###[Shougo/neocomplcache.vim](https://github.com/Shougo/neocomplcache.vim)

    自动补全，演示请见项目主页


4. ####[Raimondi/delimitMate](https://github.com/Raimondi/delimitMate)

   必装，输入引号,括号时,自动补全

   对python的docstring 三引号做了处理(只处理""", '''暂时没配，可以自己加)

   演示

   ![delimitmate](https://github.com/wklken/gallery/blob/master/vim/delimate.gif?raw=true)

5. ####[godlygeek/tabular](https://github.com/godlygeek/tabular)

   选装，代码格式化用的，code alignment

        [sd]
        ,a=  按等号切分格式化
        ,a:  按逗号切分格式化

6. ####[terryma/vim-expand-region](https://github.com/terryma/vim-expand-region)

   选装，visual mode selection
   视图模式下可伸缩选中部分，用于快速选中某些块

        [sd]
        = 增加选中范围(+/=按键)
        - 减少选中范围(_/-按键)

   演示（直接取链到其github图)

   ![expand-region](https://raw.github.com/terryma/vim-expand-region/master/expand-region.gif)

7. ####[vim-multiple-cursors](https://github.com/terryma/vim-multiple-cursors)

   选装，多光标批量操作

        [sd]
        ctrl + m 开始选择
        ctrl + p 向上取消
        ctrl + x 跳过
        esc   退出

   演示(官方演示图)

   ![multiple-cursors](https://raw.github.com/terryma/vim-multiple-cursors/master/assets/example1.gif)

> 语法检查

1. ####[scrooloose/syntastic](https://github.com/scrooloose/syntastic)

   建议安装，静态语法及风格检查,支持多种语言

   修改了下标记一列的背景色,原有的背景色在solarized下太难看了…..

   演示

   ![syntastic](https://github.com/wklken/gallery/blob/master/vim/syntastic.png?raw=true)

2. ####[kevinw/pyflakes-vim](https://github.com/kevinw/pyflakes-vim)

   虽然这个的作者推荐使用syntastic,但是这个插件对于pythoner还是很需要的

   因为有一个特牛的功能,fly check,即,编码时在buffer状态就能动态查错标记,弥补syntastic只能保存和打开时检查语法错误的不足

   演示
   ![pyflakes](https://github.com/wklken/gallery/blob/master/vim/pyflakes.png?raw=true)

> 具体语言

    主要是python  其它语言以及前端的,用得少没有研究使用过
    python   golang   markdown
    需要其它语言支持的,可以到github上捞,上面很多流行的vim配置,eg. spf13-vim
    以下均为选装，根据自己需要

1. ####[python-syntax](https://github.com/hdima/python-syntax)

   使用Python建议安装，python语法高亮,就是python.vim,在github,有维护和更新

4. ####[jnwhiteh/vim-golang](https://github.com/jnwhiteh/vim-golang)

   使用golang建议安装， golang语法高亮

   golang刚入门使用,项目中还没正式开始,目前很多golang的手册有配置vim的介绍,后续有需求再弄

5. ####[plasticboy/vim-markdown](https://github.com/plasticboy/vim-markdown)

   markdown语法,编辑md文件

6. ####[pangloss/vim-javascript](https://github.com/pangloss/vim-javascript)

   偶尔会看看js,频率不高

7. ####[nono/jquery.vim](https://github.com/nono/jquery.vim)

   jquery高亮

5. ####[thiderman/nginx-vim-syntax](https://github.com/thiderman/nginx-vim-syntax)

   nginx配置文件语法高亮,常常配置服务器很有用

6. ####[Glench/Vim-Jinja2-Syntax](https://github.com/Glench/Vim-Jinja2-Syntax)

   jinja2 语法高亮


> 其它扩展增强

    根据自身需求自取配置,不需要的话自己注解

1. ####[vim-scripts/TaskList.vim](https://github.com/vim-scripts/TaskList.vim)

   查看并快速跳转到代码中的TODO列表

   重构代码时一般通读,标记修改位置,非常实用

        [sd]
        ,td 打开todo列表

   演示

   ![tasklist](https://github.com/wklken/gallery/blob/master/vim/tasklist.gif?raw=true)

2. ####[tpope/vim-fugitive](https://github.com/tpope/vim-fugitive)

   git插件

   不是很习惯,所以用的次数太少,目前和现有配置快捷键有冲突,尚未解决


3. ####[sjl/gundo.vim](https://github.com/sjl/gundo.vim)

   编辑文件时光机

        [sd] ,h  查看文件编辑历史

