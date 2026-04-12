# 53.8 方法回调命令

`methodCallback` 模块提供的函数允许您注册一个回调，该回调将在某些 Abaqus Scripting Interface 命令即将执行时被调用。此回调允许您增强 Abaqus Scripting Interface 命令的标准行为。

例如，在以下脚本中，当某个类型为 JobType 的对象（即任何 Job 对象）的 `writeInput` 方法即将被调用时，`myCallback` 函数被执行：

```
import methodCallback
from job import JobType

def myCallback(callingObject, arguments, keywordArguments, userData):

    print 'An input file  is about to be written.'

methodCallback.addCallback(JobType, 'writeInput', myCallback)
```

**访问**

```
import methodCallback
```

### 53.8.1 addCallback(...)

此方法添加一个回调函数，该函数将在某些 Abaqus/CAE 命令即将执行时被调用。

**路径**

```
methodCallback.addCallback
```

**必需参数**

*caller*

一个对象或类型对象，指定哪个对象将触发回调函数被调用，或 SymbolicConstant ALL_TYPES。

*methodName*

一个 String，指定将在其上触发回调函数被调用的方法名称，或 SymbolicConstant ALL_METHODS。

*callback*

当匹配指定 caller 和 method name 的命令即将执行时要调用的 Python 函数。回调函数的接口定义如下：

```
def functionName(*callingMethod*, *args*, *keywordArgs*, *userData*)
```
其中：
- *callingMethod* 是调用此函数的方法。
- *args* 是传递给调用方法的非关键字参数的序列。
- *keywordArgs* 是传递给调用方法的关键字参数的字典。
- *userData* 是作为 *userData* 参数传递给 `addCallback` 方法的对象。

**可选参数**

*userData*

任何类型的数据。此数据将被传递给回调函数。默认值为 `None`。

*callAfter*

一个 Boolean，指定回调是否应在方法执行后调用（而不是在方法调用之前）。默认值为 False，表示回调应在方法执行前调用。

如果 *callAfter*=True，您还可以通过包含以下语句从回调中访问命令的返回值：

`returnValue = getMethodReturnValue()`

`getMethodReturnValue` 函数位于 `callback` 函数的全局命名空间中。

**返回值**

无。

**异常**

无。
