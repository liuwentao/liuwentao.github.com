
`Vundle`修改安装的默认路径.

在使用Vundle管理插件的时候,默认是在用户的home文件夹下面.这个本来挺方便的.但是万一如果机器不联网的时候,就会比较麻烦了.还好`Vundle`是可以修改目录的.
把文件夹放在和vimfiles一样的目录下面,就减少了很多不必要的苦恼了.


```vim
" 设定插件的位置,也可以用绝对路径
set rtp+=$VIM/vimfiles/bundle/vundle/
call vundle#rc('$VIM/vimfiles/bundle/')
```

这样话就会在gvim的目录下下载和安装插件了.