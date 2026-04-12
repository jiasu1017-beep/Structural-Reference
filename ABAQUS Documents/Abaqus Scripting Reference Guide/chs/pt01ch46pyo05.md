# 46.5 CohesiveSection 对象

CohesiveSection 对象定义内聚截面的属性。

CohesiveSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.5.1 CohesiveSection(...)

此方法创建 CohesiveSection 对象。

**Path**

```
mdb.models[*name*].CohesiveSection
session.odbs[*name*].CohesiveSection
```

**必需参数**

*name*

 String，指定存储库键。

*response*

 SymbolicConstant，指定定义内聚元素本构行为的几何假设。可选值为 TRACTION_SEPARATION、CONTINUUM 和 GASKET。

*material*

 String，指定材料名称。

**可选参数**

*initialThicknessType*

 SymbolicConstant，指定用于计算初始厚度的 方法。可选值为：
- SOLVER_DEFAULT，指定 Abaqus 将使用分析产品默认值
- GEOMETRY，指定 Abaqus 将从元素的节点坐标计算厚度。
- SPECIFY，指定 Abaqus 将使用 *initialThickness* 给定的值。

默认值为 SOLVER_DEFAULT。

*initialThickness*

 Float，指定截面的初始厚度。*initialThickness* 参数仅在 *initialThicknessType*=SPECIFY 时适用。默认值为 1.0。

*outOfPlaneThickness*

 `None` 或 Float，指定截面的面外厚度。默认值为 `None`。

**返回值**

CohesiveSection 对象。

**异常**

RangeError 和 InvalidNameError。

### 46.5.2 setValues(...)

此方法修改 CohesiveSection 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [CohesiveSection](pt01ch46pyo05.md#ker-cohesivesection-cohesivesection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 46.5.3 成员

CohesiveSection 对象的成员与 [CohesiveSection](pt01ch46pyo05.md#ker-cohesivesection-cohesivesection-pyc) 方法的参数具有相同的名称和描述。

### 46.5.4 对应分析关键字

| [*COHESIVE SECTION*](../key/key-link.md#usb-kws-mcohesivesection) |
| --- |

