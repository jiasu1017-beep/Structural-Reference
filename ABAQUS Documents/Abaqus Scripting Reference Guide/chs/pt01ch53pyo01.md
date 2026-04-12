# 53.1 SymbolicConstant 对象

SymbolicConstant 对象以可存储在回放文件中并可用作 Abaqus Scripting Interface 方法和函数的参数的方式表示字符串。按照惯例，SymbolicConstant 对象的字符串表示与其变量名相同。如果将 SymbolicConstant 对象传递给 Python `repr()` 函数，该函数返回不带引号的文本。实际上，该文本是变量，按照惯例，该变量引用 SymbolicConstant 对象。

具有相同文本的两个 SymbolicConstant 对象是同一个 Python 对象，尽管您可以将它们分配给不同的变量。Abaqus Scripting Interface 方法所需的所有 SymbolicConstant 对象都在 abaqusConstants 模块中定义。某些 SymbolicConstant 对象和 SymbolicConstant 构造函数也在 abaqus 模块中定义。SymbolicConstant 构造函数也在 symbolicConstants 模块中定义。

**访问**

```
from symbolicConstants import *
from abaqusConstants import *
```

### 53.1.1 SymbolicConstant(...)

`SymbolicConstant` 方法创建一个 SymbolicConstant 对象。

**路径**

```
SymbolicConstant
```

**必需参数**

*text*

一个 String，指定 SymbolicConstant 对象的文本。该 String 只能包含大写字母、数字或下划线，且不能以数字开头。

**可选参数**

无。

**返回值**

一个 SymbolicConstant 对象。

**异常**

无。
