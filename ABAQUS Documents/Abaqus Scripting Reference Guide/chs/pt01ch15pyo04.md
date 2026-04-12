# 15.5 DatumPoint 对象

DatumPoint 对象没有直接构造函数；它在创建 [Feature](pt01ch20pyo01.md) 对象时创建。例如，`DatumPointByCoordinate` 方法创建一个 Feature 对象，该对象创建 DatumPoint 对象。

DatumPoint 对象派生自 [Datum](pt01ch15pyo01.md) 对象。

**访问权限**

```
import part
mdb.models[*name*].parts[*name*].datums[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.datums[*i*]
mdb.models[*name*].rootAssembly.datums[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].datums[*i*]
```

### 15.5.1 成员

DatumPoint 对象具有以下成员：

*pointOn*

浮点数元组，指定位于 datum 上的点的 X、Y 和 Z 坐标。

