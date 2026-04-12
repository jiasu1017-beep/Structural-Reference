# 9.11 ConnAccelerationBC 对象

ConnAccelerationBC 对象存储连接器加速度边界条件的数据。

ConnAccelerationBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.11.1 ConnAccelerationBC(...)

此方法在线区域上创建 ConnAccelerationBC 对象。或者，也可以将边界条件应用于从组装紧固件模板模型引用的线集。

**路径**

```
mdb.models[*name*].ConnAccelerationBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

**可选参数**

*region*

边界条件所应用到的线区域。当指定了 *fastenerName* 和 *fastenerSetName* 时，此参数无效。

*fastenerName*

String，指定要应用边界条件的组装紧固件的名称。当指定了 *region* 时，此参数无效。指定此参数时，还必须指定 *fastenerSetName*。默认值为空字符串。

*fastenerSetName*

String，指定要应用边界条件的组装紧固件模板模型集的名称。当指定了 *region* 时，此参数无效。指定此参数时，还必须指定 *fastenerName*。默认值为空字符串。

*a1*

Float 或 SymbolicConstant，指定连接器局部 1 方向的加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

**注意：**虽然 *a1*、*a2*、*a3*、*ar1*、*ar2* 和 *ar3* 是可选参数，但必须至少指定其中一个。

*a2*

Float 或 SymbolicConstant，指定连接器局部 2 方向的加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*a3*

Float 或 SymbolicConstant，指定连接器局部 3 方向的加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ar1*

Float 或 SymbolicConstant，指定连接器局部 4 方向的旋转加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ar2*

Float 或 SymbolicConstant，指定连接器局部 5 方向的旋转加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ar3*

Float 或 SymbolicConstant，指定连接器局部 6 方向的旋转加速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*amplitude*

String 或 SymbolicConstant UNSET，指定幅值引用的名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*distributionType*

SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM 和 USER_DEFINED。默认值为 UNIFORM。

**返回值**

ConnAccelerationBC 对象。

**异常**

无。

### 9.11.2 setValues(...)

此方法修改创建该对象的步骤中现有 ConnAccelerationBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConnAccelerationBC](pt01ch09pyo11.md#ker-connaccelerationbc-connaccelerationbc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.11.3 setValuesInStep(...)

此方法修改指定步骤中现有 ConnAccelerationBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*a1*

Float 或 SymbolicConstant，指定连接器局部 1 方向的连接器加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*a2*

Float 或 SymbolicConstant，指定连接器局部 2 方向的连接器加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*a3*

Float 或 SymbolicConstant，指定连接器局部 3 方向的连接器加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ar1*

Float 或 SymbolicConstant，指定连接器局部 4 方向的连接器加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ar2*

Float 或 SymbolicConstant，指定连接器局部 5 方向的连接器加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ar3*

Float 或 SymbolicConstant，指定连接器局部 6 方向的连接器加速度分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*amplitude*

String 或 SymbolicConstant，指定幅值引用的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果幅值从前一个分析步骤传播，应使用 UNCHANGED。如果边界条件更改为没有幅值引用，应使用 FREED。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

无。

**异常**

无。

### 9.11.4 成员

ConnAccelerationBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*distributionType*

SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM 和 USER_DEFINED。默认值为 UNIFORM。

*fastenerName*

String，指定要应用边界条件的组装紧固件的名称。当指定了 *region* 时，此参数无效。指定此参数时，还必须指定 *fastenerSetName*。默认值为空字符串。

*fastenerSetName*

String，指定要应用边界条件的组装紧固件模板模型集的名称。当指定了 *region* 时，此参数无效。指定此参数时，还必须指定 *fastenerName*。默认值为空字符串。

*category*

SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
