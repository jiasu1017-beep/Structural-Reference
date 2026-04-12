# 22.1 Filter 对象





Filter 对象是其他 Filter 对象的抽象基类型。Filter 对象没有显式构造函数。Filter 对象的方法和成员对所有派生自 Filter 的对象都是通用的。

**访问**

```
import filter
mdb.models[*name*].filters[*name*]
import odbFilter
session.odbs[*name*].filters[*name*]
```

### 22.1.1 成员

Filter 对象具有以下成员：

*name*

一个 String，指定存储库键。此名称 ANTIALIASING 保留供程序内部生成的滤波器使用。

*cutoffFrequency*

一个 Float，指定滤波器的衰减点。可能的值为非负数。Order 不适用于 OperatorFilter。

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





