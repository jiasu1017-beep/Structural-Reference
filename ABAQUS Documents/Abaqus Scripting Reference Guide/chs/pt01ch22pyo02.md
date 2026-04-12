# 22.2 ButterworthFilter 对象





ButterworthFilter 对象定义 Butterworth 型滤波器。

ButterworthFilter 对象派生自 [Filter](pt01ch22pyo01.md) 对象。

**访问**

```
import filter
mdb.models[*name*].filters[*name*]
import odbFilter
session.odbs[*name*].filters[*name*]
```

### 22.2.1 ButterworthFilter(...)

此方法创建 ButterworthFilter 对象。

**路径**

```
mdb.models[*name*].ButterworthFilter
session.odbs[*name*].ButterworthFilter
```

**必需参数**

*name*

一个 String，指定存储库键。此名称 ANTIALIASING 保留供程序内部生成的滤波器使用。

*cutoffFrequency*

一个 Float，指定滤波器的衰减点。可能的值为非负数。Order 不适用于 OperatorFilter。

**可选参数**

*order*

一个 Int，指定滤波器传递函数的最高幂。可能的值为小于或等于 20 的非负数。Order 不适用于 OperatorFilter。默认值为 2。

*operation*

一个 SymbolicConstant，指定滤波器算子。可能的值为 NONE、MIN、MAX 和 ABS。默认值为 NONE。

*halt*

一个 Boolean，指定是否在达到指定限制时停止分析。默认值为 OFF。

*limit*

`None` 或一个 Float，指定阈值限制，根据操作类型作为输出值的上限或下限，或当使用 Halt 时用于停止分析的界限。默认值为 `None`。

*invariant*

一个 SymbolicConstant，指定应用滤波的不变量。可能的值为 NONE、FIRST 和 SECOND。默认值为 NONE。

**返回值**

一个 ButterworthFilter 对象。

**异常**

InvalidNameError 和 RangeError。

### 22.2.2 setValues(...)

此方法修改 ButterworthFilter 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ButterworthFilter](pt01ch22pyo02.md#ker-butterworthfilter-butterworthfilter-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 22.2.3 成员

ButterworthFilter 对象具有与 [ButterworthFilter](pt01ch22pyo02.md#ker-butterworthfilter-butterworthfilter-pyc) 方法的参数相同的名称和描述的成员。

### 22.2.4 对应的分析关键字

| [*FILTER*](../key/key-link.md#usb-kws-mfilter) |
| --- |





