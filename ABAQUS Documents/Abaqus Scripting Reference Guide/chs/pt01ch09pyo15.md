# 9.15 ConnVelocityBC 对象

ConnVelocityBC 对象存储连接器速度边界条件的数据。

ConnVelocityBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.15.1 ConnVelocityBC(...)

此方法在线区域上创建 ConnVelocityBC 对象。或者，也可以将边界条件应用于从组装紧固件模板模型引用的线集。

**路径**

```
mdb.models[*name*].ConnVelocityBC
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

*v1*

Float 或 SymbolicConstant，指定连接器局部 1 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

**注意：**虽然 *v1*、*v2*、*v3*、*vr1*、*vr2* 和 *vr3* 是可选参数，但必须至少指定其中一个。

*v2*

Float 或 SymbolicConstant，指定连接器局部 2 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*v3*

Float 或 SymbolicConstant，指定连接器局部 3 方向的速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*vr1*

Float 或 SymbolicConstant，指定连接器局部 4 方向的旋转速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*vr2*

Float 或 SymbolicConstant，指定连接器局部 5 方向的旋转速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*vr3*

Float 或 SymbolicConstant，指定连接器局部 6 方向的旋转速度分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*amplitude*

String 或 SymbolicConstant UNSET，指定幅值引用的名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*distributionType*

SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM 和 USER_DEFINED。默认值为 UNIFORM。

**返回值**

ConnVelocityBC 对象。

**异常**

无。

### 9.15.2 setValues(...)

此方法修改创建该对象的步骤中现有 ConnVelocityBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConnVelocityBC](pt01ch09pyo15.md#ker-connvelocitybc-connvelocitybc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.15.3 setValuesInStep(...)

此方法修改指定步骤中现有 ConnVelocityBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*v1*

Float 或 SymbolicConstant，指定连接器局部 1 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*v2*

Float 或 SymbolicConstant，指定连接器局部 2 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*v3*

Float 或 SymbolicConstant，指定连接器局部 3 方向的速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*vr1*

Float 或 SymbolicConstant，指定连接器局部 4 方向的旋转速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*vr2*

Float 或 SymbolicConstant，指定连接器局部 5 方向的旋转速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*vr3*

Float 或 SymbolicConstant，指定连接器局部 6 方向的旋转速度分量。SymbolicConstant 的可能值为 SET 和 FREED。

*amplitude*

String 或 SymbolicConstant，指定幅值引用的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果幅值从前一个分析步骤传播，应使用 UNCHANGED。如果边界条件更改为没有幅值引用，应使用 FREED。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

无。

**异常**

无。

### 9.15.4 成员

ConnVelocityBC 对象可以具有以下成员：

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
