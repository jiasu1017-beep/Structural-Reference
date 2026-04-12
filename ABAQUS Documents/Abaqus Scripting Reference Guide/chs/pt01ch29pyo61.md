# 29.61 Hyperfoam 对象

Hyperfoam 对象为超弹性泡沫指定弹性属性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].hyperfoam
import odbMaterial
session.odbs[*name*].materials[*name*].hyperfoam
```

### 29.61.1 Hyperfoam(...)

此方法创建 Hyperfoam 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Hyperfoam
session.odbs[*name*].materials[*name*].Hyperfoam
```

**必需参数**

无。

**可选参数**

*testData*

Boolean，指定是否提供测试数据。默认值为 OFF。

*poisson*

`None` 或 Float，指定材料有效泊松比，![](../graphics/ker_eqn00164.gif)。此参数仅在 *testData*=ON 时有效。默认值为 `None`。

*n*

Int，指定应变势能的阶数。可能的值为 1 ≤ *n* ≤ 6。默认值为 1。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*moduli*

SymbolicConstant，指定材料常数的时间依赖性。可能的值为 INSTANTANEOUS 和 LONG_TERM。默认值为 LONG_TERM。

*table*

Float 元组序列，指定下述项目。此参数仅在 *testData*=OFF 时有效。默认值为空序列。

**表格数据**

对于 ![](../graphics/ker_eqn00088.gif) 的值，表格数据中的项目指定以下内容：
- 对于从 1 到 ![](../graphics/ker_eqn00088.gif) 的 ![](../graphics/ker_eqn00270.gif)，![](../graphics/ker_eqn00268.gif) 和 ![](../graphics/ker_eqn00269.gif)。
- ![](../graphics/ker_eqn00284.gif)。
- 温度（如果数据依赖于温度）。在 Abaqus/Explicit 分析中，4 ≤ *n* ≤ 6 时不允许温度依赖。

**返回值**

Hyperfoam 对象。

**异常**

RangeError。

### 29.61.2 setValues(...)

此方法修改 Hyperfoam 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Hyperfoam](pt01ch29pyo61.md#ker-hyperfoam-hyperfoam-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.61.3 成员

Hyperfoam 对象的成员与 [Hyperfoam](pt01ch29pyo61.md#ker-hyperfoam-hyperfoam-pyc) 方法的参数具有相同的名称和描述。

此外，Hyperfoam 对象可以具有以下成员：

*biaxialTestData*

[BiaxialTestData](pt01ch29pyo04.md) 对象。

*volumetricTestData*

[VolumetricTestData](pt01ch29pyo110.md) 对象。

*planarTestData*

[PlanarTestData](pt01ch29pyo76.md) 对象。

*simpleShearTestData*

[SimpleShearTestData](pt01ch29pyo91.md) 对象。

*uniaxialTestData*

[UniaxialTestData](pt01ch29pyo101.md) 对象。

### 29.61.4 对应的分析关键字

| [*HYPERFOAM](../key/key-link.md#usb-kws-mhyperfoam) |
| --- |
