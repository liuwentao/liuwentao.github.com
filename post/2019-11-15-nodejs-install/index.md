
从[官网](https://nodejs.org/en/download/current/)下载zip包


规划如下的路径

- ./nodejs/node
- ./nodejs/global
- ./nodejs/cache


将zip解压到`./nodejs/node`目录。并将路径添加到`%PATH%`中。
修改`.npmrc`中的路径。增加如下内容：
```ini
prefix=D:\soft\nodejs\global
cache=D:\soft\nodejs\cache
regitry=http://npmreg.mirrors.ustc.edu.cn/
```

顺便把nodejs的镜像也改了。