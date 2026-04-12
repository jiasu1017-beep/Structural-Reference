# 46.23 SurfaceSection 对象





SurfaceSection 对象定义表面截面的属性。

SurfaceSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.23.1 SurfaceSection(...)

此方法创建 SurfaceSection 对象。

**路径**

```
mdb.models[*name*].SurfaceSection
session.odbs[*name*].SurfaceSection
```

**必要参数**

*name*

String，指定存储库键。

**可选参数**

*useDensity*

Boolean，指定是否使用 *density* 的值。默认值为 OFF。

*density*

Float，指定要应用于此截面的密度值。默认值为 0.0。

**返回值**

SurfaceSection 对象。

**异常**

RangeError 和 InvalidNameError。

### 46.23.2 成员

SurfaceSection 对象的成员与 [SurfaceSection](pt01ch46pyo23.md#ker-surfacesection-surfacesection-pyc) 方法的参数具有相同的名称和描述。

此外，SurfaceSection 对象可以具有以下成员：

*rebarLayers*

[RebarLayers](pt01ch46pyo19.md) 对象，指定增强属性。

### 46.23.3 对应分析关键字

| [*SURFACE SECTION](../key/key-link.md#usb-kws-msurfacesection) |
| --- |


