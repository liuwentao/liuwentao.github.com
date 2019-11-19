
### 拼音加加输入法

拼音加加是一个挺好的输入法,虽然作者一直不更新输入法,虽然在windows8上不能算是一个全功能的输入法.但是好用...

#### 优点

* 对双拼的良好支持
* 辅助码不奇特,有些输入法的辅助码奇特的一塌糊涂.加加的辅助码基本没有重新记忆过.
* 使用的时间长,词库已经很符合自己的习惯了.
* 词库可以支持很大的,有几百万的词库可选.
* 神奇的命令直达
#### 缺点

* 不能在多台机器间同步
* 不支持微软最新的输入法框架,导致在winodws8上面不能在`Metro`界面上使用.

### 加加同步的方案

加加论坛上面有一个同步的解决办法.使用的是`批处理`的方式.但是那个分的太细了.自己也用不了那么多.平时就是需要把词库同步,整个输入法目录同步的机会估计很少.`bat`这东东自己也不熟悉.最后用了`AutoHotKey`做了一个替代的方案.

	:::ahk
	EnvGet, syncDir, sync
	EnvGet, softDir, soft
	EnvGet, uprofile, userprofile
	if syncDir =
	    MsgBox,没有配置同步盘的环境变量.
	if softDir =
	    MsgBox,没有配置软件的环境变量

	vtype =ciku
	if 0 >= 1
	{
	 vtype = %1%
	}
	if vtype = ciku
	{
		
		FileCopyDir, %uprofile%\appdata\locallow\jjbxb, %syncDir%\Nuts\backup\jjbxb\save, 1
		FileRemoveDir, %syncDir%\Nuts\backup\jjbxb\save\tmp,1
		MsgBox,备份到网盘成功
	}else if vtype = all
	{
		FileCopyDir, %softDir%\jjbxb, %syncDir%\Nuts\backup\jjbxb, 1
		FileCopyDir, %uprofile%\appdata\locallow\jjbxb, %syncDir%\Nuts\backup\jjbxb\save, 1
		FileRemoveDir, %syncDir%\Nuts\backup\jjbxb\save\tmp,1
		MsgBox,全部备份成功
	}
	else if vtype = rall
	{
		FileCopyDir, %syncDir%\Nuts\backup\jjbxb, %softDir%\jjbxb, 1
		FileCopyDir, %syncDir%\Nuts\backup\jjbxb\save, %uprofile%\appdata\locallow\jjbxb, 1
		MsgBox,全部恢复成功
	}
	else if vtype = rciku
	{
		FileCopyDir, %syncDir%\Nuts\backup\jjbxb\save,%uprofile%\appdata\locallow\jjbxb 1
		MsgBox,从网盘恢复成功
	}

其中用到了两个环境变量,`soft`是自己常用软件的存放位置.`sync`是同步网盘存放的位置.需要在环境变量里面提前设置一下.AHK的去参数的地方还是挺好玩的...

```
Scripts support command line parameters. The format is:

AutoHotkey.exe [Switches] [Script Filename] [Script Parameters]
And for compiled scripts, the format is:

CompiledScript.exe [Switches] [Script Parameters]
```
参数的信息使用数字获得,`0`表示参数的个数.从`1`开始代表参数的内容了.
```AutoHotKey
if 0 < 3  ; The left side of a non-expression if-statement is always the name of a variable.
{
    MsgBox This script requires at least 3 incoming parameters but it only received %0%.
    ExitApp
}
```
ahk的语法还是真实很奇特.autoit这方面就好多了.

网盘使用了[坚果云](https://jianguoyun.com/‎).原因就是增量同步,且客户端不想百度和腾讯那么搞的花里胡哨的.我就需要他静静的同步文件就可以了...

#### 配置加加

在加加的自定义编码库中加入如下的信息
```ini
;测试备份功能
bfsj=/*$X[备份词库]
.\sync.ahk
ciku*/
bfsj=/*$X[恢复词库]
.\sync.ahk
rciku*/
bfsj=/*$X[备份整个加加]
.\sync.ahk
all*/
bfsj=/*$X[恢复整个加加]
.\sync.ahk
rall*/
```

#### 注意事项

* ahk编译成exe以后,会被某些杀毒软件爆毒.请自觉加入到忽略列表.