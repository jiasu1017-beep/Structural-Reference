# 59.2 ButterworthFilter 对象







ButterworthFilter 对象定义 Butterworth 类型过滤器。

ButterworthFilter 对象派生自 [Filter](pt02ch59pyo01.md) 对象。

**访问**

```
filterApi.filters()[*name*]
```

### 59.2.1 ButterworthFilter(...)

此方法创建 ButterworthFilter 对象。

**路径**

```
filterApi.ButterworthFilter
```

**原型**

```
odb_ButterworthFilter&
ButterworthFilter(const odb_String& name,
                  double cutoffFrequency,
                  int order,
                  const odb_String& operation,
                  bool halt,
                  odb_Union limit,
                  const odb_String& invariant);
```

**必需参数**

*name*

一个 odb_String，指定 repository 键。此名称 ANTIALIASING 保留供程序内部生成的过滤器使用。

*cutoffFrequency*

一个 Double，指定过滤器的衰减点。可能的值为非负数。Order 不适用于 OperatorFilter。

**可选参数**

*order*

一个 Int，指定滤波器传递函数的最高幂。可能的值为小于或等于 20 的非负数。Order 不适用于 OperatorFilter。默认值为 2。

*operation*

一个 odb_String，指定过滤器运算符。可能的值为 "NONE"、"MIN"、"MAX" 和 "ABS"。默认值为 "NONE"。

*halt*

一个 Boolean，指定在达到指定限制时是否停止分析。默认值为 false。

*limit*

字符串 "NONE" 或一个 Double，指定阈值限制、输出值的上限或下限（取决于操作），或使用 Halt 时的分析停止界限。默认值为 "NONE"。

*invariant*

一个 odb_String，指定应用过滤的不变量。可能的值为 "NONE"、"FIRST" 和 "SECOND"。默认值为 "NONE"。

**返回值**

ButterworthFilter 对象。

**异常**

InvalidNameError 和 RangeError。

### 59.2.2 setValues(...)

此方法修改 ButterworthFilter 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [ButterworthFilter](pt02ch59pyo02.md#ker-butterworthfilter-butterworthfilter-cpp) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

RangeError。

### 59.2.3 成员

ButterworthFilter 对象具有与 [ButterworthFilter](pt02ch59pyo02.md#ker-butterworthfilter-butterworthfilter-cpp) 方法的参数具有相同名称和描述的成员。

### 59.2.4 对应的分析关键字

| [*FILTER*](../key/key-link.md#usb-kws-mfilter) |
| --- |

