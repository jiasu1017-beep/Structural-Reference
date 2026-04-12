# 15.2 DatumAxis 对象

DatumAxis 对象没有直接构造函数；它在创建 [Feature](pt01ch20pyo01.md) 对象时创建。例如，`DatumAxisByCylFace` 方法创建一个 Feature 对象，该对象创建 DatumAxis 对象。

DatumAxis 对象派生自 [Datum](pt01ch15pyo01.md) 对象。

**访问权限**

```
import part
mdb.models[*name*].parts[*name*].datums[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.datums[*i*]
mdb.models[*name*].rootAssembly.datums[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].datums[*i*]
```

### 15.2.1 成员

DatumAxis 对象具有以下成员：

*pointOn*

浮点数元组，指定位于 datum 上的点的 X、Y 和 Z 坐标。

*direction*

浮点数元组，指定三个浮点数序列，指定轴的方向。

