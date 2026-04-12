# 25.2 AcousticImpedance 对象

AcousticImpedance 对象用于定义声学以及耦合声学-结构分析中的表面阻抗信息或非反射边界。

AcousticImpedance 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.2.1 AcousticImpedance(...)

此方法创建一个 AcousticImpedance 对象。

**路径**

```
mdb.models[*name*].AcousticImpedance
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 AcousticImpedance 对象的步骤名称。

*surface*

[Region](pt01ch45pyo03.md) 对象，指定声学边界表面。

**可选参数**

*definition*

 SymbolicConstant，指定要定义的声阻抗类型。可能的值为 TABULAR 和 NONREFLECTING。默认值为 TABULAR。

*interactionProperty*

字符串，指定与此交互关联的 [AcousticImpedanceProp](pt01ch25pyo03.md) 对象。

*nonreflectingType*

 SymbolicConstant，指定非反射几何类型。可能的值为 PLANE、IMPROVED、CIRCULAR、SPHERICAL、ELLIPTICAL 和 PROLATE。默认值为 PLANE。

此参数仅在 *definition*=NONREFLECTING 时有效。

*radius*

浮点数，指定定义边界表面的圆或球的半径。默认值为 1.0。

此参数仅在 *definition*=NONREFLECTING 且 *nonreflectingType*=CIRCULAR 或 SPHERICAL 时有效。

*semimajorAxis*

浮点数，指定定义边界表面的椭圆或长球体的长半轴长度。默认值为 1.0。

此参数仅在 *definition*=NONREFLECTING 且 *nonreflectingType*=ELLIPTICAL 或 PROLATE 时有效。

*eccentricity*

浮点数，指定定义边界表面的椭圆或长球体的偏心率。默认值为 0.0。

此参数仅在 *definition*=NONREFLECTING 且 *nonreflectingType*=ELLIPTICAL 或 PROLATE 时有效。

*centerCoordinates*

三个浮点数组成的序列，指定定义边界表面的椭圆或长球体中心的 X、Y 和 Z 坐标。默认值为 (0, 0, 0)。

此参数仅在 *definition*=NONREFLECTING 且 *nonreflectingType*=ELLIPTICAL 或 PROLATE 时有效。

*directionCosine*

三个浮点数组成的序列，指定定义边界表面的椭圆或长球体主轴的方向余弦的 X、Y 和 Z 分量。默认值为 (0, 0, 1)。

此参数仅在 *definition*=NONREFLECTING 且 *nonreflectingType*=ELLIPTICAL 或 PROLATE 时有效。

**返回值**

AcousticImpedance 对象。

**异常**

无。

### 25.2.2 setValues(...)

此方法修改创建 AcousticImpedance 对象的步骤中现有 AcousticImpedance 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [AcousticImpedance](pt01ch25pyo02.md#ker-acousticimpedance-acousticimpedance-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.2.3 setValuesInStep(...)

此方法修改指定步骤中现有 AcousticImpedance 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

*interactionProperty*

字符串，指定与此交互关联的 [AcousticImpedanceProp](pt01ch25pyo03.md) 对象。

**返回值**

无。

**异常**

无。

### 25.2.4 成员

AcousticImpedance 对象的成员与 [AcousticImpedance](pt01ch25pyo02.md#ker-acousticimpedance-acousticimpedance-pyc) 方法的参数具有相同的名称和描述。

### 25.2.5 对应的分析关键字

| [*SIMPEDANCE](../key/key-link.md#usb-kws-hsimpedance) |
| --- |



