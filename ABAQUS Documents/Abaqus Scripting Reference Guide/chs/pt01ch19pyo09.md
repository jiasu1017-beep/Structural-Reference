# 19.9 Inertia 对象









Inertia 对象是 [HeatCapacitance](pt01ch19pyo08.md)、[NonstructuralMass](pt01ch19pyo10.md) 和 [PointMassInertia](pt01ch19pyo12.md) 的抽象基类型。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.inertias[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.inertias[*name*]
```

### 19.9.1 resume()

此方法恢复先前被抑制的惯性。

**参数**

无。

**返回值**

无

**异常**

无。

### 19.9.2 suppress()

此方法抑制惯性。

**参数**

无。

**返回值**

无

**异常**

无。

### 19.9.3 成员

Inertia 对象具有以下成员：

*name*

一个 String，指定存储库键。

*suppressed*

一个 Boolean，指定惯性是否被抑制。默认值为 OFF。





