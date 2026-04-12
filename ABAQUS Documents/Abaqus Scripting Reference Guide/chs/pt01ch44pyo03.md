# 44.3 CompositePly 对象

CompositePly 对象定义复合铺层中的材料层。

**访问**

```
import section
mdb.models[*name*].parts[*name*].compositeLayups[*i*].plies[*i*]
```

### 44.3.1 CompositePly(...)

此方法创建 CompositePly 对象。

**Path**

```
mdb.models[*name*].parts[*name*].compositeLayups[*name*].CompositePly
```

**必需参数**

*thickness*

 Float，指定截面层的厚度。

*region*

 [Region](pt01ch45pyo03.md) 对象，指定复合铺层适用的区域。

*material*

 String，指定铺层的材料名称。

**可选参数**

*orientationValue*

 Float，指定截面层的相对取向。默认值为 0.0。

*orientationType*

 SymbolicConstant，指定用于定义相对取向的方法。如果 *orientationType*=SPECIFY_ORIENT，则需要 *orientationValue* 参数。如果 *orientationType*=CSYS，则需要 *orientation* 参数。可选值为 CSYS、SPECIFY_ORIENT、ANGLE_0、ANGLE_45、ANGLE_90 和 ANGLE_NEG45。默认值为 ANGLE_0。

*thicknessType*

 SymbolicConstant，指定用于定义厚度的方法。如果 *thicknessType*=SPECIFY_THICKNESS，则需要 *thickness* 参数。默认值为 SPECIFY_THICKENESS。

*numIntPts*

 Int，指定通过截面层使用的积分点数量。此参数仅在 *preIntegrate*=OFF 时有效。默认值为 3。

*axis*

 SymbolicConstant，指定圆柱或球形 datum 坐标系的轴，围绕该轴应用额外旋转。对于壳，此轴也是壳法线。*axis* 参数仅在、为 *orientation* 提供了有效参考时适用。可选值为 AXIS_1、AXIS_2 和 AXIS_3。默认值为 AXIS_1。

*angle*

 Float，指定额外旋转的角度。*angle* 参数仅在、为 *orientation* 提供了有效参考时适用。默认值为 0.0。

*additionalRotationType*

 SymbolicConstant，指定用于描述当指定了有效取向时的额外旋转的方法。使用 *orientationType*=ANGLE_0 和 *additionalRotationType*=ROTATION_FIELD 为此 CompositePly 指定离散旋转字段。可选值为 ROTATION_NONE、ROTATION_ANGLE 和 ROTATION_FIELD。默认值为 ROTATION_NONE。

*plyName*

 String，指定此截面层的铺层标识符。默认值为空字符串。

*orientation*

 SymbolicConstant None 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定该层相对取向的坐标系参考。默认值为 None。

*additionalRotationField*

 String，指定额外旋转字段的名称。默认值为空字符串。

**返回值**

CompositePly 对象。

**异常**

AbaqusException。

### 44.3.2 成员

CompositePly 对象的成员与 [CompositePly](pt01ch44pyo03.md#ker-compositeply-compositeply-pyc) 方法的参数具有相同的名称和描述。

