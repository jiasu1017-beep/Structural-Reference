# 42.7 IMAField 对象

IMAField 是用于为 [MaterialAssignment](pt01ch42pyo11.md) 预定义场定义材料实例名称体积分数的对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*].fieldList
```

### 42.7.1 成员

IMAField 对象可以具有以下成员：

*region*

 [Region](pt01ch45pyo03.md) 对象，指定将应用体积分数的所选零件实例的子区域。

*discFieldList*

字符串元组，指定包含体积分数数据的离散字段的名称。元组的长度对应于材料实例名称的数量，由指定的欧拉截面建立。

