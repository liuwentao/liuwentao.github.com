
### 安装git

安装官的就ok了。

### 安装zsh

在`套件中心`的 `设置->套件来源` 上添加[synocommunity](http://packages.synocommunity.com/).

之后在`社群`里面找到`Z shell with modules`并安装

### 安装oh-my-zsh

参考[oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)上的安装方法。

    sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

### 修改用户shell

 打开 `/etc/passwd`,将其中用户对应的`shell`从`bash`换成`zsh`。

### 修改PATH
在`~/.zshrc`添加如下的记录
```
export PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/syno/sbin:/usr/syno/bin:/usr/local/sbin:/usr/local/bin
```
之后重新加载下`source ~/.zshrc`就可以了。
