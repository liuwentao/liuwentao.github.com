
### 吐槽
最近在搞公司的一个小项目.抱着`挖大坑`的想法,使用了`Node.js`和`redis`.其中的`redis`是自己一直想使用的.负责的有一个数据接口,累死累活的想尽了各种办法去优化代码,如果能够使用类似`redis`这样的`NOSQL`会轻松好多.可惜,`安全第一`.

### Node.js

Node.js配置环境什么的还是挺简单的.由于微软的原因,Node.js对Windows有了很好的支持.

#### 安装nodejs
 
安装`nodejs`的话,可以通过官网提供的 msi安装包来安装,但是这样安装的话,不能很好的控制不同的版本.所以最好的办法还是自己来控制了.
下载已经编译好的`nodejs`版本.
 
```
http://nodejs.org/dist/
```
 
如下的操作创建好目录关系
 
``` bat
cd D:\soft
mkdir nodejs
cd nodejs
mkdir node
mkdir npm-global
mkdir npm-cache
```
然后将下载到的nodejs的压缩包解压到node目录中
#### 安装npm
从`http://nodejs.org/dist/npm/` 这下载需要的npm地址.
然后解压到node目录.
 
#### 设置环境变量
 
在系统的path里面加入nodejs的目录.
 
可以通过`echo %path%`来检查设定是否正确.

#### 比较好玩的modules

##### Express
[Express](http://expressjs.com/).算是目前最主流的一个Node.js平台下面的web框架了.有各种页面模版可以支持.学习和使用的成本都是很低的.
##### log4js
[log4js](http://log4js.berlios.de/index.html)log4X的一个变种了.基本上使用和配置都和log4X的其它系列差不多.挺顺手的.不过尽量在万不得已的情况下在写日志.Node.js这种非阻塞的东东,在写日志方面的确没有什么太大的优势.