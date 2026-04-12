# 15.3 DatumCsys 对象

DatumCsys 对象没有直接构造函数；它在创建 [Feature](pt01ch20pyo01.md) 对象时创建。例如，`DatumCsysByOffset` 方法创建一个 Feature 对象，该对象创建 DatumCsys 对象。

DatumCsys 对象派生自 [Datum](pt01ch15pyo01.md) 对象。

**访问权限**

```
import part
mdb.models[*name*].parts[*name*].datums[*i*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.datums[*i*]
mdb.models[*name*].rootAssembly.connectorOrientations[*i*].localCsys1
mdb.models[*name*].rootAssembly.connectorOrientations[*i*].localCsys2
mdb.models[*name*].rootAssembly.datums[*i*]
mdb.models[*name*].rootAssembly.instances[*name*].datums[*i*]
import odbAccess
session.odbs[*name*].rootAssembly.connectorOrientations[*i*].localCsys1
session.odbs[*name*].rootAssembly.connectorOrientations[*i*].localCsys2
```

### 15.3.1 成员

DatumCsys 对象具有以下成员：

*coordSysType*

符号常量，指定坐标系的类型。可能的值为 CARTESIAN、CYLINDRICAL 和 SPHERICAL。

*origin*

[DatumPoint](pt01ch15pyo05.md) 对象，指定坐标系的原点。

*axis1*

[DatumAxis](pt01ch15pyo02.md) 对象，指定坐标系的 1 方向。

*axis2*

[DatumAxis](pt01ch15pyo02.md) 对象，指定坐标系的 2 方向。

*axis3*

[DatumAxis](pt01ch15pyo02.md) 对象，指定坐标系的 3 方向。

