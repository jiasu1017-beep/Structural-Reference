# 46.8 ConnectorSection 对象

ConnectorSection 对象描述连接器的连接类型和行为。

ConnectorSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.8.1 ConnectorSection(...)

此方法创建 ConnectorSection 对象。

**Path**

```
mdb.models[*name*].ConnectorSection
session.odbs[*name*].ConnectorSection
```

**必需参数**

*name*

String，指定存储库键。

**可选参数**

*assembledType*

SymbolicConstant，指定组装连接类型。可选值为：
- NONE
- BEAM
- BUSHING
- CVJOINT
- CYLINDRICAL
- HINGE
- PLANAR
- RETRACTOR
- SLIPRING
- TRANSLATOR
- UJOINT
- WELD

默认值为 NONE。

如果 *translationalType* 或 *rotationalType* 被赋予 NONE 以外的值，则不能包含 *assembledType* 参数。*assembledType*、*translationalType* 或 *rotationalType* 中至少有一个必须被赋予 NONE 以外的值。

*rotationalType*

SymbolicConstant，指定基本旋转连接类型。可选值为：
- NONE
- ALIGN
- CARDAN
- CONSTANT_VELOCITY
- EULER
- FLEXION_TORSION
- FLOW_CONVERTER
- PROJECTION_FLEXION_TORSION
- REVOLUTE
- ROTATION
- ROTATION_ACCELEROMETER
- UNIVERSAL

默认值为 NONE。

如果 *assembledType* 被赋予 NONE 以外的值，则不能包含 *rotationalType* 参数。*assembledType*、*translationalType* 或 *rotationalType* 中至少有一个必须被赋予 NONE 以外的值。

*translationalType*

SymbolicConstant，指定基本平移连接类型。可选值为：
- NONE
- ACCELEROMETER
- AXIAL
- CARTESIAN
- JOIN
- LINK
- PROJECTION_CARTESIAN
- RADIAL_THRUST
- SLIDE_PLANE
- SLOT

默认值为 NONE。

如果 *assembledType* 被赋予 NONE 以外的值，则不能包含 *translationalType* 参数。*assembledType*、*translationalType* 或 *rotationalType* 中至少有一个必须被赋予 NONE 以外的值。

*integration*

SymbolicConstant，指定分析使用的时间积分方案。此参数仅适用于 Abaqus/Explicit 分析。可选值为 UNSPECIFIED、IMPLICIT 和 EXPLICIT。默认值为 UNSPECIFIED。

*u1ReferenceLength*

`None` 或 Float，指定与相对运动第一分量本构响应相关的参考长度。默认值为 `None`。

*u2ReferenceLength*

`None` 或 Float，指定与相对运动第二分量本构响应相关的参考长度。默认值为 `None`。

*u3ReferenceLength*

`None` 或 Float，指定与相对运动第三分量本构响应相关的参考长度。默认值为 `None`。

*ur1ReferenceAngle*

`None` 或 Float，指定与相对运动第四分量本构响应相关的参考角度（度）。默认值为 `None`。

*ur2ReferenceAngle*

`None` 或 Float，指定与相对运动第五分量本构响应相关的参考角度（度）。默认值为 `None`。

*ur3ReferenceAngle*

`None` 或 Float，指定与相对运动第六分量本构响应相关的参考角度（度）。默认值为 `None`。

*massPerLength*

`None` 或 Float，指定皮带材料每单位参考长度的质量。此参数仅在 *assembledType*=SLIPRING 时适用，且在这种情况下必须指定。默认值为 `None`。

*contactAngle*

`None` 或 Float，指定皮带缠绕在节点 b 处的接触角度。此参数仅适用于 Abaqus/Explicit 分析，且仅在 *assembledType*=SLIPRING 时适用。默认值为 `None`。

*materialFlowFactor*

Float，指定在节点 b 处的材料流动缩放因子。此参数仅在 *assembledType*=RETRACTOR 或 *rotationalType*=FLOW_CONVERTER 时适用。默认值为 1.0。

*regularize*

Boolean，指定是否对与 *behaviorOptions* 关联的所有表格数据进行正则化。此参数仅适用于 Abaqus/Explicit 分析。默认值为 ON。

*defaultTolerance*

Boolean，指定是否为所有与 *behaviorOptions* 关联的表格数据使用默认正则化容差。此参数仅在 Abaqus/Explicit 分析中适用，且仅在 *regularize*=ON 时适用。默认值为 ON。

*regularization*

Float，指定与所有与 *behaviorOptions* 关联的表格数据一起使用的正则化增量。此参数仅在 Abaqus/Explicit 分析中适用，且仅在 *regularize*=ON 和 *defaultTolerance*=OFF 时适用。默认值为 0.03。

*extrapolation*

SymbolicConstant，指定用于所有与 *behaviorOptions* 关联的表格数据的外推技术。可选值为 CONSTANT 和 LINEAR。默认值为 CONSTANT。

*behaviorOptions*

[ConnectorBehaviorOptionArray](pt01ch12pyo01.md) 对象。

**返回值**

ConnectorSection 对象。

**异常**

InvalidNameError 和 RangeError。

### 46.8.2 setValues(...)

此方法修改 ConnectorSection 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConnectorSection](pt01ch46pyo08.md#ker-connectorsection-connectorsection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

RangeError。

### 46.8.3 成员

ConnectorSection 对象的成员与 [ConnectorSection](pt01ch46pyo08.md#ker-connectorsection-connectorsection-pyc) 方法的参数具有相同的名称和描述。

### 46.8.4 对应分析关键字

| [*CONNECTOR SECTION*](../key/key-link.md#usb-kws-mconnectorsection) |
| --- |
| [*CONNECTOR BEHAVIOR*](../key/key-link.md#usb-kws-mconnectorbehavior) |
| [*CONNECTOR CONSTITUTIVE REFERENCE*](../key/key-link.md#usb-kws-mconnectorconstref) |
