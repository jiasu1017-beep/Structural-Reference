# 19.1 EngineeringFeature 对象









EngineeringFeature 对象是各种特定工程特征存储库的容器。EngineeringFeature 对象没有显式构造函数或方法。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures
```

### 19.1.1 assignSeam(...)

此方法沿边缘或面创建裂缝。

**必需参数**

*regions*

一个 [Region](pt01ch45pyo03.md) 对象序列，指定裂缝的区域。[Region](pt01ch45pyo03.md) 对象必须是面或边缘。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 19.1.2 deleteSeam(...)

此方法删除裂缝。

**必需参数**

*regions*

一个 [Region](pt01ch45pyo03.md) 对象序列，指定裂缝的区域。[Region](pt01ch45pyo03.md) 对象必须是面或边缘。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 19.1.3 成员

EngineeringFeature 对象可具有以下成员：

*inertias*

[Inertia](pt01ch19pyo09.md) 对象的存储库。

*cracks*

[Crack](pt01ch19pyo04.md) 对象的存储库。

*fasteners*

[Fastener](pt01ch19pyo07.md) 对象的存储库。

*springDashpots*

[SpringDashpot](pt01ch19pyo13.md) 对象的存储库。





