# 53.9 删除对象回调命令







`deleteObjectCallback` 模块提供的方法允许您注册一个回调，该回调将在指定的 Abaqus Scripting Interface 对象即将被删除时被调用。此回调允许您在对象被删除之前检查它。

例如，在以下脚本中，当任何 `Job` 对象即将被删除时，`myCallback` 函数被执行：

```
import deleteObjectCallback

def myCallback(path, userData):

    print 'About to delete', path

deleteObjectCallback.addCallback(path='mdb.jobs[*]')
```

**访问**

```
import deleteObjectCallback
```

### 53.9.1 deleteObjectCallback(...)

此方法添加一个回调函数，该函数将在指定的 Abaqus Scripting Interface 对象即将被删除时被调用。仅当使用 Python 语句 `del object` 删除对象时才会调用回调。当使用 Abaqus Scripting Interface 命令（如 `mdb.models[name].parts[name].deleteFeature()`）删除对象时，不会调用回调。

**路径**

```
deleteObjectCallback.addCallback
```

**必需参数**

*callback*

当匹配指定路径的对象即将被删除时要调用的 Python 函数。回调函数的接口定义如下：

```
def functionName(*objectPath*, *userData*)
```
其中：
- *objectPath* 是即将被删除的对象的路径。
- *userData* 是作为 *userData* 参数传递给 `addCallback` 方法的对象。

*path*

一个 String，指定对象的路径或 SymbolicConstant ANY。您可以在路径中包含通配符来指定要匹配的模式。有效路径的示例包括：

```
path='mdb.models[*]'
path='mdb.models[\'Axle*\'].parts[*]'
path='mdb.models[*].materials[*]'

```

**可选参数**

*userData*

任何类型的数据。此数据将被传递给回调函数。默认值为 `None`。

*includeChildren*

一个 Boolean，指定当由 *path* 参数指定的对象拥有的对象即将被删除时是否应调用回调。默认值为 False。

**返回值**

None

**异常**

None。

