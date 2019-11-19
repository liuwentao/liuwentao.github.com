

在写`autohotkey`脚本的时候,遇到的一个比较大的困扰就是每次修改完成以后还要去托盘上刷新一下.最近在开发node.js应用的时候,用到一个利器`nodemon` 这个神器除了能够监控`node.js`的程序以外.还可以监控一些脚本语言的.

	nodemon --exec "d:\dev\autohotkey\autohotkey.exe" d:\dev\script\test.ahk -e ahk

这样一来,如果修改了test.ahk.会自动退出之前的.然后重新启动一个.也算起到了刷新的作用.