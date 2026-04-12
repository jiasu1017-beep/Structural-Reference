# 59.1 Filter 对象







Filter 对象是其他 Filter 对象的抽象基类型。Filter 对象没有构造函数。Filter 对象的方法和成员是所有派生自 Filter 的对象的通用成员。

**访问**

```
filterApi.filters()[*name*]
```

### 59.1.1 成员

Filter 对象具有以下成员：

**原型**

```
odb_String name() const;
double cutoffFrequency() const;
int order() const;
odb_String operation() const;
bool halt() const;
odb_Union limit() const;
odb_String invariant() const;
```

*name*

一个 odb_String，指定 repository 键。此名称 ANTIALIASING 保留供程序内部生成的过滤器使用。

*cutoffFrequency*

一个 Double，指定过滤器的衰减点。可能的值为非负数。Order 不适用于 OperatorFilter。

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

