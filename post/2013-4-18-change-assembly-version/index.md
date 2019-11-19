
部门搞了自动构建.以前自己也用过`ccnet`之类的工具.有很多的版本号递增的规则很是方便.可惜我们不是用类似的工具,所以版本号这块就只能自己手动来修改了.不过这个修改也挺麻烦的.后来就考虑写一个小工具来完成版本号的修改.本来打算用`C#`做一个.但是还依赖`.Net Framework`.刚好最近看了一下`AutoIt`,就用这个练习了一下.于是就做出了这么一个东东.

```autoit
#NoTrayIcon
#region ;**** Directives created by AutoIt3Wrapper_GUI ****
#AutoIt3Wrapper_Icon=ti.ico
#AutoIt3Wrapper_Run_Tidy=y
#endregion ;**** Directives created by AutoIt3Wrapper_GUI ****
#include <File.au3>
#include <Array.au3>

Local $path = 'D:\code\batchAgent'
Local $aVersion = '1.0.0.3'
Local $aRecords
If $CmdLine[0] >= 2 Then
	$path = $CmdLine[1]
	$aVersion = $CmdLine[2]
Else
	MsgBox(0, "Warn", '测试模式')
EndIf
Local $var = StringRight($path, 1)

If StringCompare($var, '\') <> 0 Then
	$path = $path & '\'
EndIf

Local $FileList = _FileListToArray($path, '*', 2)


For $i = 1 To $FileList[0]

	If _FileReadToArray($path & $FileList[$i] & '\Properties\AssemblyInfo.cs', $aRecords) Then
		;_ArrayDisplay($aRecords, "$aRecords")
		For $y = 1 To $aRecords[0]
			Local $result = StringRegExp($aRecords[$y], "^\[assembly\:\s\w*Version")

			If $result > 0 Then
				;用正则替换
				Local $sOutput = StringRegExpReplace($aRecords[$y], '\"([\d{1,}?\.]*)\"', '"' & $aVersion & '"')
				$aRecords[$y] = $sOutput

			EndIf
		Next
		Local $hFile = FileOpen($path & $FileList[$i] & '\Properties\AssemblyInfo.cs', 2 + 128) ; 1 = append
		For $y = 1 To $aRecords[0]
			Local $hFileWrite = FileWrite($hFile, $aRecords[$y] & @CRLF)
		Next
		FileClose($hFile)
	EndIf
Next
```
用上面的脚本编译一个exe,然后传递一个项目的路径和版本号就可以把Assembly的版本号改掉了.