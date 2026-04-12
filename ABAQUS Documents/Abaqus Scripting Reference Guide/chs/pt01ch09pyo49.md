# 9.49 VelocityBC 对象

VelocityBC 对象存储速度边界条件的数据。

VelocityBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.49.1 VelocityBC(...)

此方法创建 VelocityBC 对象。

**路径**

```
mdb.models[*name*].VelocityBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*fieldName*

String，指定与此边界条件关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*fieldName* 参数仅在 *distributionType*=FIELD 时适用。默认值为空字符串。

*v1*

Float 或 SymbolicConstant，指定 1 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

**注意：**虽然 *v1*、*v2*、*v3*、*vr1*、*vr2* 和 *vr3* 是可选参数，但必须至少指定其中一个。

*v2*

Float 或 SymbolicConstant，指定 2 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*v3*

Float 或 SymbolicConstant，指定 3 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*vr1*

Float 或 SymbolicConstant，指定关于 1 方向的旋转速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*vr2*

Float 或 SymbolicConstant，指定关于 2 方向的旋转速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*vr3*

Float 或 SymbolicConstant，指定关于 3 方向的旋转速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*amplitude*

String 或 SymbolicConstant UNSET，指定幅值引用的名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

*distributionType*

SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM、USER_DEFINED 和 FIELD。默认值为 UNIFORM。

**返回值**

VelocityBC 对象。

**异常**

无。

### 9.49.2 setValues(...)

此方法修改创建该对象的步骤中现有 VelocityBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [VelocityBC](pt01ch09pyo49.md#ker-velocitybc-velocitybc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.49.3 setValuesInStep(...)

此方法修改指定步骤中现有 VelocityBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*v1*

Float 或 SymbolicConstant，指定 1 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*v2*

Float 或 SymbolicConstant，指定 2 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*v3*

Float 或 SymbolicConstant，指定 3 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*vr1*

Float 或 SymbolicConstant，指定关于 1 方向的旋转速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*vr2*

Float 或 SymbolicConstant，指定关于 2 方向的旋转速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*vr3*

Float 或 SymbolicConstant，指定关于 3 方向的旋转速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*amplitude*

String 或 SymbolicConstant，指定幅值引用的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果幅值从前一个分析步骤传播，应使用 UNCHANGED。如果边界条件更改为没有幅值引用，应使用 FREED。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

无。

**异常**

无。

### 9.49.4 成员

VelocityBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*distributionType*

SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM、USER_DEFINED 和 FIELD。默认值为 UNIFORM。

*fieldName*

String，指定与此边界条件关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*fieldName* 参数仅在 *distributionType*=FIELD 时适用。默认值为空字符串