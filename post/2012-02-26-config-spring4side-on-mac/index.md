
spring是一个很强悍的框架.早已脱离了最早的orm.国内有人做了一个springside的框架,其实就是将spring和一些工具整合起来,做的示例.挺方便的.

#### 前期准备

*   JDK
*   MAVEN
*   eclipse
*   M2Eclipse
*   git

由于装了homebrew,所以安装maven很方便  
` brew install maven `   
同样安装git  
` brew install git `   
至于eclipse和M2eclipse的安装.就靠自己吧…

##### 获取代码

springside4已经迁移到github上面.所以,可以通过如下方式得到最新的代码:  
`git clone https://github.com/springside/springside4.git`

##### 配置环境

由于使用了maven,此处的环境配置应该很简单.不必为各种jar包冲突所烦恼.安装上m2e以后,就可以将项目导入到eclipse里面了.但是有一个问题,刚导入的项目,由于jar包的缺失.无法通过编译. 此处需要作如下处理  
分别进入

<pre>cd modules/core
mvn install
cd ..
cd extension
mvn install
cd ..
cd parent
mvn install
cd ..
cd ..
cd examples/mini-service
mvn install
cd ..
cd mini-web
mvn install
cd ..
cd showcase
mvn install
</pre>

这样就基本就可以通过编译了.但是在完成以上步骤以后.还是有可能出现如下的几个错误提示

<pre>Project configuration is not up-to-date with pom.xml. Run project configuration update
</pre>

第一个解决办法使用quick fix.然后就没有问题了.其实就是更新了项目的配置信息.

为什么会有这样的问题,原因是由于m2e和maven之间的配置不一样导致的.可以通过如下两个插件其中任意一个完成.

*   [Build Helper Maven Plugin][1]
*   [apt-m2e][2]

至此就可以将springside4的开发环境配置完成.

 [1]: http://mojo.codehaus.org/build-helper-maven-plugin/
 [2]: https://apt-m2e.googlecode.com/