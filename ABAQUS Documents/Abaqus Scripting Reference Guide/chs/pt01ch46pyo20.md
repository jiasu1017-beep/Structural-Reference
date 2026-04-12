# 46.20 SectionLayer 对象





SectionLayer 对象定义复合壳中的材料层。

**访问**

```
import section
mdb.models[*name*].parts[*name*].compositeLayups[*i*].section.layup[*i*]
mdb.models[*name*].sections[*name*].layup[*i*]
import odbSection
session.odbs[*name*].sections[*name*].layup[*i*]
```

### 46.20.1 SectionLayer(...)

此方法创建 SectionLayer 对象。

**路径**

```
section.SectionLayer
```

```
odbSection.SectionLayer
```

**必要参数**

*thickness*

Float，指定截面层的厚度。

*material*

String，指定截面层材料的名称。

**可选参数**

*orientAngle*

Float 或 String，指定截面层的相对方向。Float 指定角度方向；String 指定用户子程序方向名称。如果指定了 String，则使用用户子程序方向，否则 Float 值用作角度方向。默认值为 0.0。

*numIntPts*

Int，指定通过截面使用的积分点数量。此参数仅在父 [CompositeShellSection](pt01ch46pyo06.md) 对象上的 *preIntegrate* 参数设置为 ON 时有效。默认值为 3。

*axis*

SymbolicConstant，指定圆柱形或球形基准坐标系中应用额外旋转的轴。对于壳，此轴也是壳法线。这仅在提供了有效的方向参考时适用。可能的值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_3。

*angle*

Float，指定额外旋转的角度。这仅在提供了有效的方向参考时适用。默认值为 0.0。

*additionalRotationType*

SymbolicConstant，指定在指定有效方向时描述额外旋转的方法。可能的值为 ROTATION_NONE、ROTATION_ANGLE 和 ROTATION_FIELD。默认值为 ROTATION_NONE。

*thicknessType*

SymbolicConstant，指定描述厚度的方法。可能的值为 THICKNESS_MAGNITUDE 和 THICKNESS_DISCRETE_FIELD。默认值为 THICKNESS_MAGNITUDE。

*plyName*

String，指定此截面层的层标识符。默认值为 ""。

*orientation*

SymbolicConstant None 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定此层相对方向的坐标系参考。如果此参考有效，则使用它作为层的相对方向，否则按上述方式使用 *orientAngle*。默认值为 None。

*additionalRotationField*

String，指定描述额外旋转的字段名称。默认值为 ""。

*thicknessField*

String，指定描述厚度的字段名称。默认值为 ""。

**返回值**

SectionLayer 对象。

**异常**

无。

### 46.20.2 成员

SectionLayer 对象的成员与 [SectionLayer](pt01ch46pyo20.md#ker-sectionlayer-sectionlayer-pyc) 方法的参数具有相同的名称和描述。

### 46.20.3 对应分析关键字

| [*SHELL SECTION](../key/key-link.md#usb-kws-mshellsection) |
| --- |
| [*SHELL GENERAL SECTION](../key/key-link.md#usb-kws-mshellgensect) |


