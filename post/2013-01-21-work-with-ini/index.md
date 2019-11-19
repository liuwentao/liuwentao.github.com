
# Ini的陷阱

测试的时候发现了一个问题.`ini配置文件`第一行如果未`section`的话.是无法读到的.解决办法也有就是空一行就万事大吉了.

今天下午刚好又遇到了.然后就想着把这个解决了.之前为什么不想动的原因是因为这个读取使用的Windows的接口.很有可能这东西就有这么个问题…

大家读取ini的方法其实基本上都是一样的,用windows的api.网上也有各种例子.大差不差吧.出问题就处在[GetProfileSection](http://msdn.microsoft.com/zh-cn/library/windows/desktop/ms724363.aspx)
这个接口上了.第一行如果是小节[section]的话,是无法读取的…

# NIni
想想读写ini,用C#单写其实也不差.后来发现有一个[Nini](http://nini.sourceforge.net)的框架.就很好的实现了配置文件的读写.比Windows API的方式方便多了.

Nini的特性
Features

* Multiple configuration types INI, XML, Registry, and command line
* Strong variable types<br/> String, int, float, etc. Eliminates casts
* Set and save<br/> Add, remove, edit, and save configs
* Lightweight and fast<br/> Small footprint, built for speed
* Merging<br/> Merge several configs into one
* 100% free<br/> Free and open source code
* Value aliases<br/> Add aliases for unclear variables
* Key value replacement<br/> Replaces values with other key values
* Cross platform<br/> Run on .NET/Mono Linux/Mac/Windows
* INI parser<br/> Contains a 100% managed INI parser
* Fully documented<br/> See the Nini manual and API reference
* Unlimited files/sources<br/> Loads an unlimited number of files
* Compact Framework<br/> Supports the .NET Compact Framework
* Command line application<br/> Has a command-line configuration editor
* Mature and stable<br/> Over 140 unit tests


以上这些特性简直完美了.特别是自带配置编辑器.合并配置文件,强类型,替换,文档全.这些都是很不错的.
.
接下来这一周希望把Nini的源码看一遍.以后工作中项目涉及到配置文件的,不出意外应该都会使用到这个神器