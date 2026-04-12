# 2.13 VelocityAdaptiveMeshConstraint 对象





VelocityAdaptiveMeshConstraint 对象存储任意拉格朗日欧拉（ALE）样式速度自适应网格约束的数据。

VelocityAdaptiveMeshConstraint 对象派生自 [AdaptiveMeshConstraint](pt01ch02pyo01.md) 对象。

**访问**

```
import step
mdb.models[*name*].adaptiveMeshConstraints[*name*]
```

### 2.13.1 VelocityAdaptiveMeshConstraint(...)

此方法创建一个 VelocityAdaptiveMeshConstraint 对象。

**路径**

```
mdb.models[*name*].VelocityAdaptiveMeshConstraint
```

**必需参数**

*name*

一个 String，指定自适应网格约束仓库键。

*createStepName*

一个 String，指定创建自适应网格约束的步骤名称。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用自适应网格约束的区域。

**可选参数**

*v1*

一个 Float 或 SymbolicConstant，指定 1 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

**注：**虽然 *v1*、*v2*、*v3*、*vr1*、*vr2* 和 *vr3* 是可选参数，但必须至少指定其中之一。

*v2*

一个 Float 或 SymbolicConstant，指定 2 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*v3*

一个 Float 或 SymbolicConstant，指定 3 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*vr1*

一个 Float 或 SymbolicConstant，指定关于 1 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*vr2*

一个 Float 或 SymbolicConstant，指定关于 2 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*vr3*

一个 Float 或 SymbolicConstant，指定关于 3 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*amplitude*

一个 String 或 SymbolicConstant UNSET，指定幅值参考的名称。如果自适应网格约束没有幅值参考，应使用 UNSET。默认值为 UNSET。您应该仅在指定步骤有效时才提供 *amplitude* 参数。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定自适应网格约束自由度的局部坐标系。如果 *localCsys*=`None`，则在全局坐标系中定义自由度。默认值为 `None`。

*motionType*

一个 SymbolicConstant，指定网格运动与底层材料的关系。可能的值为 INDEPENDENT、FOLLOW 和 USER_DEFINED。默认值为 INDEPENDENT。

**返回值**

一个 VelocityAdaptiveMeshConstraint 对象。

**异常**

无。

### 2.13.2 setValues(...)

此方法修改创建它的步骤中现有 VelocityAdaptiveMeshConstraint 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [VelocityAdaptiveMeshConstraint](pt01ch02pyo13.md#ker-velocityadaptivemeshconstraint-velocityadaptivemeshc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无

**异常**

无。

### 2.13.3 setValuesInStep(...)

此方法修改指定步骤中现有 VelocityAdaptiveMeshConstraint 对象的传播数据。

**必需参数**

*stepName*

一个 String，指定修改自适应网格约束的步骤名称。

**可选参数**

*v1*

一个 Float 或 SymbolicConstant，指定 1 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*v2*

一个 Float 或 SymbolicConstant，指定 2 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*v3*

一个 Float 或 SymbolicConstant，指定 3 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*vr1*

一个 Float 或 SymbolicConstant，指定关于 1 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*vr2*

一个 Float 或 SymbolicConstant，指定关于 2 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*vr3*

一个 Float 或 SymbolicConstant，指定关于 3 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*amplitude*

一个 String 或 SymbolicConstant，指定幅值参考的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果幅值是从前一个分析步骤传播的，应使用 UNCHANGED。如果自适应网格约束被更改为没有幅值参考，应使用 FREED。您应该仅在指定步骤有效时才提供 *amplitude* 参数。

**返回值**

无

**异常**

无。

### 2.13.4 成员

VelocityAdaptiveMeshConstraint 对象可以具有以下成员：

*name*

一个 String，指定自适应网格约束仓库键。

*category*

一个 SymbolicConstant，指定自适应网格约束的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用自适应网格约束的区域。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定自适应网格约束自由度的局部坐标系。如果 *localCsys*=`None`，则在全局坐标系中定义自由度。默认值为 `None`。




