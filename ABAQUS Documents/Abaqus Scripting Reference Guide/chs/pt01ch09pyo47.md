# 9.47 VelocityBaseMotionBC 对象

VelocityBaseMotionBC 对象存储速度基准运动边界条件的数据。

VelocityBaseMotionBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.47.1 VelocityBaseMotionBC(...)

此方法创建 VelocityBaseMotionBC 对象。

**路径**

```
mdb.models[*name*].VelocityBaseMotionBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*dof*

SymbolicConstant，指定约束的自由度。SymbolicConstant 的可能值为 U1、U2、U3、UR1、UR2、UR3。默认值为 U1。

**可选参数**

*amplitudeScaleFactor*

Float，指定幅值曲线的缩放因子。默认值为 1.0。

*centerOfRotation*

[ModelDot](pt01ch07pyo12.md) 对象，指定包含一个旋转中心的元组。默认值为全局原点。此参数仅适用于 *dof*=UR1、UR2 或 UR3 的情况。

*correlation*

[CorrelationArray](pt01ch03pyo04.md) 对象。

*secondaryBase*

String，指定与此边界条件关联的 [SecondaryBaseBC](pt01ch09pyo39.md) 对象的名称。默认值为空字符串。

*useComplex*

Boolean，指定是否为幅值定义给出的基准运动记录定义虚部（平面外）部分。默认值为 OFF。

*amplitude*

String 或 SymbolicConstant UNSET，指定幅值引用的名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

VelocityBaseMotionBC 对象。

**异常**

无。

### 9.47.2 setValues(...)

此方法修改创建该对象的步骤中现有 VelocityBaseMotionBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [VelocityBaseMotionBC](pt01ch09pyo47.md#ker-velocitybasemotionbc-velocitybasemotionbc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.47.3 setValuesInStep(...)

此方法修改指定步骤中现有 VelocityBaseMotionBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*amplitude*

String 或 SymbolicConstant，指定幅值引用的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果幅值从前一个分析步骤传播，应使用 UNCHANGED。如果边界条件更改为没有幅值引用，应使用 FREED。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

无。

**异常**

无。

### 9.47.4 成员

VelocityBaseMotionBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*amplitudeScaleFactor*

Float，指定幅值曲线的缩放因子。默认值为 1.0。

*useComplex*

Boolean，指定是否为幅值定义给出的基准运动记录定义虚部（平面外）部分。默认值为 OFF。

*centerOfRotation*

[ModelDot](pt01ch07pyo12.md) 对象，指定包含一个旋转中心的元组。默认值为全局原点。此参数仅适用于 *dof*=UR1、UR2 或 UR3 的情况。

*correlation*

[CorrelationArray](pt01ch03pyo04.md) 对象。

*secondaryBase*

String，指定与此边界条件关联的 [SecondaryBaseBC](pt01ch09pyo39.md) 对象的名称。默认值为空字符串。

*category*

SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
