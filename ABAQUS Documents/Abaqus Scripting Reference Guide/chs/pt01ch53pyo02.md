# 53.2 AbaqusBoolean 对象

AbaqusBoolean 对象的用法与 SymbolicConstant 对象类似。如果将 AbaqusBoolean 对象传递给 Python `repr()` 函数，该函数返回不带引号的文本。实际上，该文本是变量，按照惯例，该变量引用 AbaqusBoolean 对象。

AbaqusBoolean 对象的值为 0 或 1，并且可以在 `if` 语句中测试 AbaqusBoolean 对象。您可以将 AbaqusBoolean 对象用作方法的参数来替代 1 或 0。相反，如果您将 0 或 1 传递给期望 Boolean 参数的 Abaqus Scripting Interface 方法，0 或 1 将被强制转换为适当的 AbaqusBoolean 值。

AbaqusBoolean 对象只有两个可能的值：1 和 0。您可以从 symbolicConstants 模块或 abaqus 模块导入这两个值。期望 AbaqusBoolean 对象的 Abaqus Scripting Interface 命令也将接受 Python bool（True、False）或 Python int（1、0）。

**访问**

```
from symbolicConstants import *
from abaqusConstants import *
```

### 53.2.1 AbaqusBoolean(...)

`AbaqusBoolean` 方法创建一个 AbaqusBoolean 对象。

**路径**

```
AbaqusBoolean
```

**必需参数**

*value*

一个 Int，指定 AbaqusBoolean 对象将为 true 还是 false 进行测试。可能的值为 0 和 1，它们将分别创建 `AbaqusBoolean` 方法 OFF 和 ON。

**可选参数**

无。

**返回值**

一个 AbaqusBoolean 对象。

**异常**

无。
