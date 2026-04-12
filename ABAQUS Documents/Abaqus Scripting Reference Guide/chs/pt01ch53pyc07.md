# 53.11 自定义命令







以下命令用于在 Abaqus 日志文件中记录用户定义的命令。

### 53.11.1 journalMethodCall(...)

此函数可由用户定义的命令使用，用于在 Abaqus 日志文件中记录自身。

例如：

```
def setValues( self, **kargs ):
        for arg,value in kargs.items():
            setattr(self, arg, value)
        from abaqus import journalMethodCall
        objPath = '%s[%r]' % (self.reposPath, self.name)
        journalMethodCall(objPath, 'setValues', (), kargs)

```

**注意：**如果命令使用内置的 Abaqus Scripting Interface 命令更改了 mdb，则命令不应调用 `journalMethodCall`，因为内置命令默认会被记录。更改 mdb customData 的命令是应调用 `journalMethodCall` 的命令类型的一个示例。

**路径**

```
journalMethodCall
```

**必需参数**

*objectPath*

一个 String，指定对象的路径。

*methodName*

一个 String，指定方法的名称。

*args*

一个序列，指定要写入日志文件的位置参数。

*kargs*

一个 Python dict 对象，指定要写入日志文件的关键字参数。

**可选参数**

None。

**返回值**

None

**异常**

None。

