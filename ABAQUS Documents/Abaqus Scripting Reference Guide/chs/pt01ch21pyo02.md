# 21.2 AnalyticalField 对象





AnalyticalField 对象是其他 AnalyticalField 对象的抽象基类型。AnalyticalField 对象没有显式构造函数。AnalyticalField 对象的方法和成员对所有派生自 AnalyticalField 的对象都是通用的。

AnalyticalField 对象派生自 [Field](pt01ch21pyo01.md) 对象。

**访问**

```
import fields
mdb.models[*name*].analyticalFields[*name*]
```

### 21.2.1 成员

AnalyticalField 对象可以具有以下成员：

*name*

一个 String，指定存储库键。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定场的局部坐标系。如果 *localCsys*=`None`，则场在全局坐标系中定义。默认值为 `None`。

*description*

一个 String，指定场的描述。默认值为空字符串。





