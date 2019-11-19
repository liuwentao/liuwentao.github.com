## Ack

`Ack`是类似于grep的一个搜索工具,主要是面向程序员的.可以快速方便的从大量的代码中查找你需要的信息.默认不会去搜索`SCM`产生的文件.相对于

## 优势

*   速度快
*   命令简单
*   支持正则
*   纯perl,跨平台.安装简单

## 安装

安装的话很简单,机器只要安装了`perl`的话,简单的一个命令 
<pre>cpan App:Ack
</pre> 就可以搞定了. windwos下面需要安装

[strawberryperl][1],然后执行如上的命令就可以了.

Mac下面使用homebrew执行: 
<pre>brew install ack
</pre>

## 语法

可以参考[Ack][2]的语法介绍,很简单的.

<pre>ack --csharp todo -i -l
</pre>

如上命令就可以将代码中包含todo的以列表的形式列出.很是方便快速.

 [1]: http://strawberryperl.com/
 [2]: http://betterthangrep.com/