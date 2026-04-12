# 29.67 LowDensityFoam 对象

LowDensityFoam 对象指定低密度泡沫的属性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].lowDensityFoam
import odbMaterial
session.odbs[*name*].materials[*name*].lowDensityFoam
```

### 29.67.1 LowDensityFoam(...)

此方法创建 LowDensityFoam 对象。

**路径**

```
mdb.models[*name*].materials[*name*].LowDensityFoam
session.odbs[*name*].materials[*name*].LowDensityFoam
```

**必需参数**

无。

**可选参数**

*elementRemoval*

Boolean，指定是否在超过最大主拉应力时移除单元。此参数仅在定义了 *maxAllowablePrincipalStress* 时有效。默认值为 OFF。

*maxAllowablePrincipalStress*

`None` 或 Float，指定最大允许主拉应力。默认值为 `None`。

*extrapolateStressStrainCurve*

Boolean，指定是否在超过最大应变率时外推应力-应变曲线。默认值为 OFF。

*strainRateType*

SymbolicConstant，指定用于本构计算的应变率度量。可能的值为 PRINCIPAL 和 VOLUMETRIC。默认值为 VOLUMETRIC。

*mu0*

Float，指定松弛系数 ![](../graphics/ker_eqn00288.gif)。默认值为 10–4。

*mu1*

Float，指定松弛系数 ![](../graphics/ker_eqn00070.gif)。默认值为 0.510–2。

*alpha*

Float，指定松弛系数 ![](../graphics/ker_eqn00090.gif)。默认值为 2.0。

**返回值**

LowDensityFoam 对象。

**异常**

RangeError。

### 29.67.2 setValues(...)

此方法修改 LowDensityFoam 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [LowDensityFoam](pt01ch29pyo67.md#ker-lowdensityfoam-lowdensityfoam-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.67.3 成员

LowDensityFoam 对象的成员与 [LowDensityFoam](pt01ch29pyo67.md#ker-lowdensityfoam-lowdensityfoam-pyc) 方法的参数具有相同的名称和描述。

此外，LowDensityFoam 对象可以具有以下成员：

*uniaxialTensionTestData*

[UniaxialTestData](pt01ch29pyo101.md) 对象。

*uniaxialCompressionTestData*

[UniaxialTestData](pt01ch29pyo101.md) 对象。

### 29.67.4 对应的分析关键字

| [*LOW DENSITY FOAM](../key/key-link.md#usb-kws-mlowdensfoam) |
| --- |
