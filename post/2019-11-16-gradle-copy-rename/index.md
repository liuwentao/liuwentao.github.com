
这两年的项目中，一直使用`gradle`.在处理依赖的时候能够更简洁。在处理发布环境的时候也更可控一些。最近就遇到了这样的一个问题。
维护了一个修改历史，需要把这个文件打包进每个子模块。把这个放到`build`之前。这样就可以把修改历史打包到各模块了。


```kotlin
task copyVersionMd(type: Copy) {
    from('../')
    into ('../xx-module/src/main/resources/')
    include 'version.md'
    rename { String fileName ->
        fileName.replace("version.md", "history.md")
    }
}
```