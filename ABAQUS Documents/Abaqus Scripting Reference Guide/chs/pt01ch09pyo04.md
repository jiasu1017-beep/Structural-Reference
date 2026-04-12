# 9.4 AccelerationBC 对象

AccelerationBC 对象存储加速度边界条件的数据。

AccelerationBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.4.1 AccelerationBC(...)

此方法创建一个 AccelerationBC 对象。

**路径**

```
mdb.models[*name*].AccelerationBC
```

**必需参数**

*name*

一个 String，指定边界条件存储库键。

*createStepName*

一个 String，指定创建边界条件的步骤名称。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用边界条件的区域。

**可选参数**

*fieldName*

一个 String，指定与此边界条件关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*fieldName* 参数仅在 *distributionType*=FIELD 时适用。默认值为空字符串。

*a1*

一个 Float 或 SymbolicConstant，指定 1 方向上的加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

**注：**虽然 *a1*、*a2*、*a3*、*ar1*、*ar2* 和 *ar3* 是可选参数，但必须至少指定其中一个。

*a2*

一个 Float 或 SymbolicConstant，指定 2 方向上的加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*a3*

一个 Float 或 SymbolicConstant，指定 3 方向上的加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ar1*

一个 Float 或 SymbolicConstant，指定关于 1 方向的旋转加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ar2*

一个 Float 或 SymbolicConstant，指定关于 2 方向的旋转加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ar3*

一个 Float 或 SymbolicConstant，指定关于 3 方向的旋转加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*amplitude*

一个 String 或 SymbolicConstant UNSET，指定振幅引用的名称。如果边界条件没有振幅引用，应使用 UNSET。默认值为 UNSET。只有当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

*distributionType*

一个 SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM、USER_DEFINED 和 FIELD。默认值为 UNIFORM。

**返回值**

一个 AccelerationBC 对象。

**异常**

无。

### 9.4.2 setValues(...)

此方法修改现有 AccelerationBC 对象在创建它的步骤中的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [AccelerationBC](pt01ch09pyo04.md#ker-accelerationbc-accelerationbc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.4.3 setValuesInStep(...)

此方法修改指定步骤中现有 AccelerationBC 对象的传播数据。

**必需参数**

*stepName*

一个 String，指定要修改边界条件的步骤名称。

**可选参数**

*a1*

一个 Float 或 SymbolicConstant，指定 1 方向上的加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*a2*

一个 Float 或 SymbolicConstant，指定 2 方向上的加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*a3*

一个 Float 或 SymbolicConstant，指定 3 方向上的加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ar1*

一个 Float 或 SymbolicConstant，指定关于 1 方向的旋转加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ar2*

一个 Float 或 SymbolicConstant，指定关于 2 方向的旋转加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ar3*

一个 Float 或 SymbolicConstant，指定关于 3 方向的旋转加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*amplitude*

一个 String 或 SymbolicConstant，指定振幅引用的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。UNCHANGED 应在振幅从先前的分析步骤传播时使用。如果边界条件要改为没有振幅引用，应使用 FREED。只有当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

无。

**异常**

无。

### 9.4.4 成员

AccelerationBC 对象可以具有以下成员：

*name*

一个 String，指定边界条件存储库键。

*distributionType*

一个 SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM、USER_DEFINED 和 FIELD。默认值为 UNIFORM。

*fieldName*

一个 String，指定与此边界条件关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*fieldName* 参数仅在 *distributionType*=FIELD 时适用。默认值为空字符串。

*category*

一个 SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用边界条件的区域。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
