# 29.60 Hyperelastic 对象

Hyperelastic 对象为近似不可压缩弹性体指定弹性属性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].hyperelastic
import odbMaterial
session.odbs[*name*].materials[*name*].hyperelastic
```

### 29.60.1 Hyperelastic(...)

此方法创建 Hyperelastic 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Hyperelastic
session.odbs[*name*].materials[*name*].Hyperelastic
```

**必需参数**

*table*

Float 元组序列，指定下述项目。此参数仅在 *testData*=OFF 时有效。

**可选参数**

*type*

SymbolicConstant，指定应变势能类型。可能的值为：
- ARRUDA_BOYCE
- MARLOW
- MOONEY_RIVLIN
- NEO_HOOKE
- OGDEN
- POLYNOMIAL
- REDUCED_POLYNOMIAL
- USER
- VAN_DER_WAALS
- YEOH
- UNKNOWN

默认值为 UNKNOWN。

*moduliTimeScale*

SymbolicConstant，指定时间响应的性质。可能的值为 INSTANTANEOUS 和 LONG_TERM。默认值为 LONG_TERM。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*n*

Int，指定应变势能的阶数。默认值为 1。

如果 *testData*=ON 且 *type*=POLYNOMIAL，*n* 只能取 1 或 2。

如果 *testData*=ON 且 *type*=OGDEN，或对于任一类型 *testData*=OFF，则 1 ≤ *n* ≤ 6。

如果 *type*=USER，则不能使用此参数。

*beta*

SymbolicConstant FITTED_VALUE 或 Float，指定不变量混合参数。此参数仅在 *testData*=ON 且 *type*=VAN_DER_WAALS 时有效。默认值为 FITTED_VALUE。

*testData*

Boolean，指定是否提供测试数据。默认值为 ON。

*compressible*

Boolean，指定超弹性材料是否可压缩。此参数仅适用于用户定义的超弹性材料。默认值为 OFF。

*properties*

Int，指定作为用户定义超弹性材料数据所需的属性值数量。默认值为 0。

*deviatoricResponse*

SymbolicConstant，指定使用哪些测试数据。可能的值为 UNIAXIAL、BIAXIAL 和 PLANAR。默认值为 UNIAXIAL。

*volumetricResponse*

SymbolicConstant，指定体积响应。可能的值为 DEFAULT、VOLUMETRIC_DATA、POISSON_RATIO 和 LATERAL_NOMINAL_STRAIN。默认值为 DEFAULT。

*poissonRatio*

Float，指定泊松比。此参数仅在 *volumetricResponse*=POISSON_RATIO 时有效。默认值为 0.0。

*materialType*

SymbolicConstant，指定材料类型。可能的值为 ISOTROPIC 和 ANISOTROPIC。默认值为 ISOTROPIC。

*anisotropicType*

SymbolicConstant，指定应变势能类型。可能的值为 FUNG_ANISOTROPIC、FUNG_ORTHOTROPIC、HOLZAPFEL 和 USER_DEFINED。默认值为 FUNG_ANISOTROPIC。

*formulation*

SymbolicConstant，指定公式类型。可能的值为 STRAIN 和 INVARIANT。默认值为 STRAIN。

*behaviorType*

SymbolicConstant，指定各向异性超弹性材料行为类型。可能的值为 INCOMPRESSIBLE 和 COMPRESSIBLE。默认值为 INCOMPRESSIBLE。

*dependencies*

Int，指定 *volumetricTable* 中数据的场变量依赖项数量。默认值为 0。

*localDirections*

Int，指定 *volumetricTable* 中数据的局部方向数量。默认值为 0。

**表格数据**

如果 *type*=ARRUDA_BOYCE，表格数据指定以下内容：
- ![](../graphics/ker_eqn00041.gif)。
- ![](../graphics/ker_eqn00264.gif)。
- ![](../graphics/ker_eqn00172.gif)。
- 温度（如果数据依赖于温度）。

如果 *type*=MOONEY_RIVLIN，表格数据指定以下内容：
- ![](../graphics/ker_eqn00265.gif)。
- ![](../graphics/ker_eqn00266.gif)。
- ![](../graphics/ker_eqn00267.gif)。
- 温度（如果数据依赖于温度）。

如果 *type*=NEO_HOOKE，表格数据指定以下内容：
- ![](../graphics/ker_eqn00265.gif)。
- ![](../graphics/ker_eqn00267.gif)。
- 温度（如果数据依赖于温度）。

如果 *type*=OGDEN，对于 ![](../graphics/ker_eqn00088.gif) 的值，表格数据指定以下内容：
- 对于从 1 到 ![](../graphics/ker_eqn00088.gif) 的 ![](../graphics/ker_eqn00270.gif)，![](../graphics/ker_eqn00268.gif) 和 ![](../graphics/ker_eqn00269.gif)。
- ![](../graphics/ker_eqn00088.gif) 个系数 ![](../graphics/ker_eqn00271.gif)。
- 温度（如果数据依赖于温度）。在 Abaqus/Explicit 分析中，4 ≤ *n* ≤ 6 时不允许温度依赖。

如果 *type*=POLYNOMIAL，对于 ![](../graphics/ker_eqn00088.gif) 的值，表格数据指定以下内容：
- 对于从 ![](../graphics/ker_eqn00274.gif) 到 ![](../graphics/ker_eqn00088.gif) 的 ![](../graphics/ker_eqn00270.gif)（其中 ![](../graphics/ker_eqn00270.gif) 从 ![](../graphics/ker_eqn00274.gif) 递减到零，且 ![](../graphics/ker_eqn00276.gif) 从零递增到 ![](../graphics/ker_eqn00274.gif)），![](../graphics/ker_eqn00273.gif)。
- ![](../graphics/ker_eqn00088.gif) 个系数 ![](../graphics/ker_eqn00271.gif)。
- 温度（如果数据依赖于温度）。在 Abaqus/Explicit 分析中，3 ≤ *n* ≤ 6 时不允许温度依赖。

如果 *type*=REDUCED_POLYNOMIAL，对于 ![](../graphics/ker_eqn00088.gif) 的值，表格数据指定以下内容：
- 对于从 1 到 ![](../graphics/ker_eqn00088.gif) 的 ![](../graphics/ker_eqn00270.gif)，![](../graphics/ker_eqn00277.gif)。
- ![](../graphics/ker_eqn00088.gif) 个系数 ![](../graphics/ker_eqn00271.gif)。
- 温度（如果数据依赖于温度）。在 Abaqus/Explicit 分析中，4 ≤ *n* ≤ 6 时不允许温度依赖。

如果 *type*=VAN_DER_WAALS，表格数据指定以下内容：
- ![](../graphics/ker_eqn00041.gif)。
- ![](../graphics/ker_eqn00264.gif)。
- ![](../graphics/ker_eqn00278.gif)。
- ![](../graphics/ker_eqn00095.gif)。
- ![](../graphics/ker_eqn00172.gif)。
- 温度（如果数据依赖于温度）。

如果 *type*=YEOH，表格数据指定以下内容：
- ![](../graphics/ker_eqn00265.gif)。
- ![](../graphics/ker_eqn00279.gif)。
- ![](../graphics/ker_eqn00280.gif)。
- ![](../graphics/ker_eqn00267.gif)。
- ![](../graphics/ker_eqn00281.gif)。
- ![](../graphics/ker_eqn00282.gif)。
- 温度（如果数据依赖于温度）。在 Abaqus/Explicit 分析中不允许温度依赖。

如果 *testData*=ON，则 `None` 对象为默认值。

**返回值**

Hyperelastic 对象。

**异常**

InvalidNameError 和 RangeError。

### 29.60.2 setValues(...)

此方法修改 Hyperelastic 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Hyperelastic](pt01ch29pyo60.md#ker-hyperelastic-hyperelastic-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.60.3 成员

Hyperelastic 对象的成员与 [Hyperelastic](pt01ch29pyo60.md#ker-hyperelastic-hyperelastic-pyc) 方法的参数具有相同的名称和描述。

此外，Hyperelastic 对象可以具有以下成员：

*biaxialTestData*

[BiaxialTestData](pt01ch29pyo04.md) 对象。

*planarTestData*

[PlanarTestData](pt01ch29pyo76.md) 对象。

*uniaxialTestData*

[UniaxialTestData](pt01ch29pyo101.md) 对象。

*volumetricTestData*

[VolumetricTestData](pt01ch29pyo110.md) 对象。

*hysteresis*

[Hysteresis](pt01ch29pyo63.md) 对象。

### 29.60.4 对应的分析关键字

| [*HYPERELASTIC](../key/key-link.md#usb-kws-mhyperelast) |
| --- |
