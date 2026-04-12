# 53.7 回调命令

这些函数用于执行 Python 命令或函数。

### 53.7.1 addImportCallback(...)

此函数定义一个在导入指定 Abaqus/CAE 模块时被调用的函数。您不能指定自定义模块。

有关更多信息，请参阅《Abaqus Scripting User's Guide》第 6.8.3 节["回调函数示例"]。

**路径**

```
addImportCallback
```

**必需参数**

*moduleName*

一个 String，指定指定 Abaqus/CAE 模块的名称。

*callback*

要调用的 Python 函数。回调函数的接口定义如下：

```
def functionName(*moduleName*, *userData*)
```
- *moduleName* 是一个 String。
- *userData* 是作为 *userData* 参数传递给 `addImportCallback` 方法的对象。

**可选参数**

*userData*

任何 Python 对象或 `None`。此对象被传递给回调函数。

**返回值**

无。

**异常**

无。

### 53.7.2 removeImportCallback(...)

此函数用于移除在 `addImportCallback` 中添加的回调。

**路径**

```
removeImportCallback
```

**必需参数**

*callback*

要调用的 Python 函数；它必须与原始调用 `addImportCallback` 时指定的 *callback* 参数相同。

*userData*

任何 Python 对象或 `None`；它必须与原始调用 `addImportCallback` 时指定的 *userData* 参数相同。

**可选参数**

无。

**返回值**

无。

**异常**

无。
