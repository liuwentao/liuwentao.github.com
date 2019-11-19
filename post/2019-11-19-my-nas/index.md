
## 何为NAS

根据百科上的说法，NAS（Network Attached Storage：网络附属存储）按字面简单说就是连接在网络上，具备资料存储功能的装置，因此也称为“网络存储器”。

也可以理解为是个人版的`DropBox`、百度网盘。有专门的硬件。

可以购买硬件或者用旧的设备来做。不过考虑稳定，功耗一般还是建议直接买个成品了。不折腾。

## 用NAS做了什么

用NAS当然主要是备份资料了，把媳妇和我的电脑上的重要资料通过NAS备份了一下。此外由于用的是群晖`DS218+`支持`Docker`。所以可玩性就比较高了。

通过`Docker`在群晖上跑了如下的服务：


- [miniflux](https://github.com/miniflux/miniflux) // rss 阅读器
- rsshub // rss服务
- [wallabag](https://wallabag.org/en) // pocket的替代
- [shaarli](https://github.com/shaarli/Shaarli) // 网站收藏
- anki-sync // 自建anki同步服务器
- gitea // git服务器
- drone // 配合gitea实现ci
- poratiner // 容器管理，不过只用来看日志了。。
- traefik // 对容器服务做反代
- bitwarden // 密码管理
- calibre-web // 书籍管理

其中RSS阅读器是刚需呀，`google reader`被关掉以后。就用[Bazqux](https://bazqux.com/)提供的服务。`TTRS`也是一个不错的选择，不过实际使用的时候，总是感觉不太灵光。

`anki-sync` anki-web在国内的同步速度简直是不可用的状态。而且有些要记录的东西也不方便放到公用的服务器上。自己搭建一套还是比较靠谱的。

`traefik`对容器内的服务做反代，不然一个个的映射端口，太麻烦了。没有这个，各种服务真的是没法愉快的玩耍了。

`btiwarden`算是目前最好的密码管理了。不折腾的一个方案了。不过还是不能替换`keepassxc`。





