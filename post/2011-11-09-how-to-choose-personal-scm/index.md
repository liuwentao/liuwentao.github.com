

自己平时会写一些代码,需要把这些代码管理起来.用svn的话,不太方便.以往的这种集中式的SCM软件,如CVS和SVN.个人用起来还是太麻烦了.svn如果在服务器down掉的情况下简直就是个杯具.自己最近绝大多数时间都是在没有网络的环境里面.那么分布式的代码管理,如GIT和Mercurial的优势就体现出来了.而且他们相对svn都有一个很强势的有点,那就是"快".

git和Mercurial是现在两个比较主流的DSCM软件了.两者之前的区别,已经有很多人介绍过了.我最终是选择了Mercurial.

原因是因为:

* 对于windows的支持.git在这面比较悲剧,中文log的支持很有问题.没有一个完美的解决办法.
* client,git的乌龟完全没有hg的乌龟好用…
* git无法和powercmd配合,这个只能说是powercmd的bug,但是,谁让现在主要使用powercmd呢…hg基本无影响.


其实最早接触的是git,也很早就在github上放了自己的几个项目.但是,毕竟自己是悲催的C#程序员….无可避免的要经常在windows环境下开发.又不可避免的要写点中文的日志.所以…不过还好,我们有Mercurial,有bitbucket.虽然bitebucket的社交性没有github的强,但是也不错了,个人免费这点挺好的.而且有私有代码库.

文中的软件地址:

* git:[http://git-scm.com/](http://git-scm.com/)
* Mercurial:[http://mercurial.selenic.com/](http://mercurial.selenic.com/)
* tortoisehg:[http://tortoisehg.org/](http://tortoisehg.org/)
* tortoisegit:[http://code.google.com/p/tortoisegit/](http://code.google.com/p/tortoisegit/)