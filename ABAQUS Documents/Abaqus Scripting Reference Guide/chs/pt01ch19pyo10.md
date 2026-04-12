# 19.10 NonstructuralMass 对象









NonstructuralMass 对象定义来自非结构特征的质量贡献到模型中。

NonstructuralMass 对象派生自 [Inertia](pt01ch19pyo09.md) 对象。

**访问**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.inertias[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.inertias[*name*]
```

### 19.10.1 NonstructuralMass(...)

此方法创建 NonstructuralMass 对象。

**路径**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.NonstructuralMass
mdb.models[*name*].rootAssembly.engineeringFeatures.NonstructuralMass
```

**必需参数**

*name*

一个 String，指定存储库键。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用质量的区域。

*units*

一个 SymbolicConstant，指定用于指定非结构质量的单位。可能的值为 TOTAL_MASS、MASS_PER_VOLUME、MASS_PER_AREA 和 MASS_PER_LENGTH。

*magnitude*

一个 Float，指定质量大小。

**可选参数**

*distribution*

一个 SymbolicConstant，指定非结构质量的分布。可能的值为 MASS_PROPORTIONAL 和 VOLUME_PROPORTIONAL。默认值为 MASS_PROPORTIONAL。

*distribution* 参数仅在 *units*=TOTAL_MASS 时适用。

**返回值**

一个 NonstructuralMass 对象。

**异常**

无。

### 19.10.2 setValues(...)

此方法修改 NonstructuralMass 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [NonstructuralMass](pt01ch19pyo10.md#ker-nonstructuralmass-nonstructuralmass-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 19.10.3 成员

NonstructuralMass 对象具有与 [NonstructuralMass](pt01ch19pyo10.md#ker-nonstructuralmass-nonstructuralmass-pyc) 方法的参数相同的名称和描述的成员。

此外，NonstructuralMass 对象还有以下成员：

*suppressed*

一个 Boolean，指定惯性是否被抑制。默认值为 OFF。

### 19.10.4 对应的分析关键字

| [*NONSTRUCTURAL MASS](../key/key-link.md#usb-kws-mnonstructuralmass) |
| --- |





