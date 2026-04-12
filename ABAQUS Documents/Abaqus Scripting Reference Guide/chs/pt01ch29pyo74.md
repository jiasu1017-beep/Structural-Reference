# 29.74 Permeability 对象

Permeability 对象定义孔隙流体渗透率。

**访问**

```
import material
mdb.models[*name*].materials[*name*].permeability
import odbMaterial
session.odbs[*name*].materials[*name*].permeability
```

### 29.74.1 Permeability(...)

此方法创建 Permeability 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Permeability
session.odbs[*name*].materials[*name*].Permeability
```

**必需参数**

*specificWeight*

Float，指定润湿液体的比重，![](../graphics/ker_eqn00296.gif)。

*inertialDragCoefficient*

Float，指定润湿液体的惯性拖曳系数，![](../graphics/ker_eqn00296.gif)。

*table*

Float 元组序列，指定下述项目。

**可选参数**

*type*

SymbolicConstant，指定渗透率类型。可能的值为 ISOTROPIC、ORTHOTROPIC、ANISOTROPIC、ISOTROPIC-CFD 和 CARMAN_KOZENY。默认值为 ISOTROPIC。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

如果 *type*=ISOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00143.gif)。
- 孔隙比，![](../graphics/ker_eqn00289.gif)。
- 温度（如果数据依赖于温度）。

如果 *type*=ORTHOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00144.gif)。
- ![](../graphics/ker_eqn00145.gif)。
- ![](../graphics/ker_eqn00146.gif)。
- 孔隙比，![](../graphics/ker_eqn00289.gif)。
- 温度（如果数据依赖于温度）。

如果 *type*=ANISOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00144.gif)。
- ![](../graphics/ker_eqn00147.gif)。
- ![](../graphics/ker_eqn00145.gif)。
- ![](../graphics/ker_eqn00148.gif)。
- ![](../graphics/ker_eqn00149.gif)。
- ![](../graphics/ker_eqn00146.gif)。
- 孔隙比，![](../graphics/ker_eqn00289.gif)。
- 温度（如果数据依赖于温度）。

如果 *type*=ISOTROPIC_CFD，表格数据指定以下内容：
- ![](../graphics/ker_eqn00143.gif)。
- 孔隙率，![](../graphics/ker_eqn00289.gif)。

如果 *type*=CARMAN_KOZENY，表格数据指定以下内容：
- Kozeny 常数，![](../graphics/ker_eqn00289.gif)。
- 孔隙颗粒半径，![](../graphics/ker_eqn00289.gif)。

**返回值**

Permeability 对象。

**异常**

RangeError。

### 29.74.2 setValues(...)

此方法修改 Permeability 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Permeability](pt01ch29pyo74.md#ker-permeability-permeability-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.74.3 成员

Permeability 对象的成员与 [Permeability](pt01ch29pyo74.md#ker-permeability-permeability-pyc) 方法的参数具有相同的名称和描述。

此外，Permeability 对象可以具有以下成员：

*saturationDependence*

[SaturationDependence](pt01ch29pyo88.md) 对象，指定材料渗透率对润湿液体饱和度的依赖性。

*velocityDependence*

[VelocityDependence](pt01ch29pyo105.md) 对象，指定材料渗透率对流体流速的依赖性。

### 29.74.4 对应的分析关键字

| [*PERMEABILITY](../key/key-link.md#usb-kws-mpermeabil) |
| --- |
