# 29.88 SaturationDependence 对象

SaturationDependence 对象指定材料渗透率对润湿液体饱和度的依赖性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].permeability.saturationDependence
import odbMaterial
session.odbs[*name*].materials[*name*].permeability.saturationDependence
```

### 29.88.1 SaturationDependence(...)

此方法创建 SaturationDependence 对象。

**路径**

```
mdb.models[*name*].materials[*name*].permeability.SaturationDependence
session.odbs[*name*].materials[*name*].permeability.SaturationDependence
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

无。

**表格数据**

- ![](../graphics/ker_eqn00362.gif)。（无量纲。）
- 饱和度，![](../graphics/ker_eqn00234.gif)。（无量纲。）

**返回值**

SaturationDependence 对象。

**异常**

RangeError。

### 29.88.2 setValues(...)

此方法修改 SaturationDependence 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SaturationDependence](pt01ch29pyo88.md#ker-saturationdependence-saturationdependence-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.88.3 成员

SaturationDependence 对象的成员与 [SaturationDependence](pt01ch29pyo88.md#ker-saturationdependence-saturationdependence-pyc) 方法的参数具有相同的名称和描述。

### 29.88.4 对应的分析关键字

| [*PERMEABILITY](../key/key-link.md#usb-kws-mpermeabil) |
| --- |
