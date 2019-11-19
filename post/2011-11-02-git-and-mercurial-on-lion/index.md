
升级到Lion GM以后,git和Mercurial都用不了了.解决办法如下:

git重装一下就可以了.

Mercurial也需要重新安装一下.

然后打开 `/usr/local/bin/hg`

`sudo vim /usr/local/bin/hg`

将

`libdir = '../../platlib/Library/Python/2.6/site-packages/'`


替换为:


`libdir = '/Library/Python/2.6/site-packages'`

即可.

这样的话,两大神器就可以继续使用了.