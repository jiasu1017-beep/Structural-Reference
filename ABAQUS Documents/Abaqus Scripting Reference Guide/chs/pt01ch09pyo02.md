# 9.2 AccelerationBaseMotionBC 对象

AccelerationBaseMotionBC 对象存储加速度基准运动边界条件的数据。

AccelerationBaseMotionBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.2.1 AccelerationBaseMotionBC(...)

此方法创建一个 AccelerationBaseMotionBC 对象。

**路径**

```
mdb.models[*name*].AccelerationBaseMotionBC
```

**必需参数**

*name*

一个 String，指定边界条件存储库键。

*createStepName*

一个 String，指定创建边界条件的步骤名称。

*dof*

一个 SymbolicConstant，指定约束的自由度。SymbolicConstant 的可能值为 U1、U2、U3、UR1、UR2、UR3。默认值为 U1。

**可选参数**

*amplitudeScaleFactor*

一个 Float，指定振幅曲线的缩放因子。默认值为 1.0。

*centerOfRotation*

一个 [ModelDot](pt01ch07pyo12.md) 对象，指定包含一个旋转中心的元组。默认值为全局原点。此参数仅适用于 *dof*=UR1、UR2 或 UR3 时。

*correlation*

一个 [CorrelationArray](pt01ch03pyo04.md) 对象。

*secondaryBase*

一个 String，指定与此边界条件关联的 [SecondaryBaseBC](pt01ch09pyo39.md) 对象的名称。默认值为空字符串。

*useComplex*

一个 Boolean，指定是否定义由振幅定义给出的基准运动记录的虚部（平面外）部分。默认值为 OFF。

*amplitude*

一个 String 或 SymbolicConstant UNSET，指定振幅引用的名称。如果边界条件没有振幅引用，应使用 UNSET。默认值为 UNSET。只有当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

一个 AccelerationBaseMotionBC 对象。

**异常**

无。

### 9.2.2 setValues(...)

此方法修改现有 AccelerationBaseMotionBC 对象在创建它的步骤中的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [AccelerationBaseMotionBC](pt01ch09pyo02.md#ker-accelerationbasemotionbc-accelerationbasemotionbc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.2.3 setValuesInStep(...)

此方法修改指定步骤中现有 AccelerationBaseMotionBC 对象的传播数据。

**必需参数**

*stepName*

一个 String，指定要修改边界条件的步骤名称。

**可选参数**

*amplitude*

一个 String 或 SymbolicConstant，指定振幅引用的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。UNCHANGED 应在振幅从先前的分析步骤传播时使用。如果边界条件要改为没有振幅引用，应使用 FREED。只有当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

无。

**异常**

无。

### 9.2.4 成员

AccelerationBaseMotionBC 对象可以具有以下成员：

*name*

一个 String，指定边界条件存储库键。

*amplitudeScaleFactor*

一个 Float，指定振幅曲线的缩放因子。默认值为 1.0。

*useComplex*

一个 Boolean，指定是否定义由振幅定义给出的基准运动记录的虚部（平面外）部分。默认值为 OFF。

*centerOfRotation*

一个 [ModelDot](pt01ch07pyo12.md) 对象，指定包含一个旋转中心的元组。默认值为全局原点。此参数仅适用于 *dof*=UR1、UR2 或 UR3 时。

*correlation*

一个 [CorrelationArray](pt01ch03pyo04.md) 对象。

*secondaryBase*

一个 String，指定与此边界条件关联的 [SecondaryBaseBC](pt01ch09pyo39.md) 对象的名称。默认值为空字符串。

*category*

一个 SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用边界条件的区域。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
