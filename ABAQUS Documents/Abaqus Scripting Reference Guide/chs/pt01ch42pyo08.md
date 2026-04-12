# 42.8 IMARegion 对象

IMARegion 是用于为 [MaterialAssignment](pt01ch42pyo11.md) 预定义场定义材料实例名称体积分数的对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*].assignmentList
```

### 42.8.1 成员

IMARegion 对象可以具有以下成员：

*region*

 [Region](pt01ch45pyo03.md) 对象，指定将应用体积分数的所选零件实例的子区域。

*fractionList*

 Float 元组，指定每个材料实例名称的体积分数。元组的长度对应于材料实例名称的数量，由指定的欧拉截面建立。

