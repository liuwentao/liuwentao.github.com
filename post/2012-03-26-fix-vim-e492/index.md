
`vim`的插件有时由于是windows下编写的原因,所以.在unix下面无法打开.报 `E492不是编辑器命令 ^M` 解决办法很简单 打开以后,执行:

<pre>:set ff=unix
:wq
</pre>

这样就可以解决了.其他编辑文件的话,建议使用`FencView`.可以自动侦测文件的编码.省去不少时间.