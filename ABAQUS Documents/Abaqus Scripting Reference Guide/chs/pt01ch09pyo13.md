# 9.13 ConnDisplacementBC 对象

ConnDisplacementBC 对象存储连接器位移/旋转边界条件的数据。

ConnDisplacementBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.13.1 ConnDisplacementBC(...)

此方法在线区域上创建 ConnDisplacementBC 对象。或者，也可以将边界条件应用于从组装紧固件模板模型引用的线集。

**路径**

```
mdb.models[*name*].ConnDisplacementBC
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

*u1*

Float、Complex 或 SymbolicConstant，指定连接器局部 1 方向的位移分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

**注意：**虽然 *u1*、*u2*、*u3*、*ur1*、*ur2* 和 *ur3* 是可选参数，但必须至少指定其中一个。

*u2*

Float、Complex 或 SymbolicConstant，指定连接器局部 2 方向的位移分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*u3*

Float、Complex 或 SymbolicConstant，指定连接器局部 3 方向的位移分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ur1*

Float、Complex 或 SymbolicConstant，指定连接器局部 4 方向的旋转分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ur2*

Float、Complex 或 SymbolicConstant，指定连接器局部 5 方向的旋转分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ur3*

Float、Complex 或 SymbolicConstant，指定连接器局部 6 方向的旋转分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*fixed*

Boolean，指定边界条件是否应在步骤开始时保持在当前值。默认值为 OFF。

*amplitude*

String 或 SymbolicConstant UNSET，指定幅值引用的名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*distributionType*

SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM 和 USER_DEFINED。默认值为 UNIFORM。

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

**返回值**

ConnDisplacementBC 对象。

**异常**

无。

### 9.13.2 setValues(...)

此方法修改创建该对象的步骤中现有 ConnDisplacementBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ConnDisplacementBC](pt01ch09pyo13.md#ker-conndisplacementbc-conndisplacementbc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.13.3 setValuesInStep(...)

此方法修改指定步骤中现有 ConnDisplacementBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*u1*

Float、Complex 或 SymbolicConstant，指定连接器局部 1 方向的位移分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*u2*

Float、Complex 或 SymbolicConstant，指定连接器局部 2 方向的位移分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*u3*

Float、Complex 或 SymbolicConstant，指定连接器局部 3 方向的位移分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ur1*

Float、Complex 或 SymbolicConstant，指定连接器局部 4 方向的旋转分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ur2*

Float、Complex 或 SymbolicConstant，指定连接器局部 5 方向的旋转分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ur3*

Float、Complex 或 SymbolicConstant，指定连接器局部 6 方向的旋转分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*amplitude*

String 或 SymbolicConstant，指定幅值引用的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果幅值从前一个分析步骤传播，应使用 UNCHANGED。如果边界条件更改为没有幅值引用，应使用 FREED。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

**返回值**

无。

**异常**

无。

### 9.13.4 成员

ConnDisplacementBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*fixed*

Boolean，指定边界条件是否应在步骤开始时保持在当前值。默认值为 OFF。

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

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
