# 9.19 DisplacementBC 对象

DisplacementBC 对象存储位移/旋转边界条件的数据。

DisplacementBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.19.1 DisplacementBC(...)

此方法创建 DisplacementBC 对象。

**路径**

```
mdb.models[*name*].DisplacementBC
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

String，指定与此边界条件关联的 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称。*fieldName* 参数仅在 *distributionType*=FIELD 或 *distributionType*=DISCRETE_FIELD 时适用。默认值为空字符串。

*u1*

Float、Complex 或 SymbolicConstant，指定 1 方向的位移分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

**注意：**虽然 *u1*、*u2*、*u3*、*ur1*、*ur2* 和 *ur3* 是可选参数，但必须至少指定其中一个。

*u2*

Float、Complex 或 SymbolicConstant，指定 2 方向的位移分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*u3*

Float、Complex 或 SymbolicConstant，指定 3 方向的位移分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ur1*

Float、Complex 或 SymbolicConstant，指定关于 1 方向的旋转位移分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ur2*

Float、Complex 或 SymbolicConstant，指定关于 2 方向的旋转位移分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*ur3*

Float、Complex 或 SymbolicConstant，指定关于 3 方向的旋转位移分量。SymbolicConstant 的可能值为 UNSET 和 SET。默认值为 UNSET。

*fixed*

Boolean，指定边界条件是否应在步骤开始时保持在当前值。默认值为 OFF。

*amplitude*

String 或 SymbolicConstant UNSET，指定幅值引用的名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*distributionType*

SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM、USER_DEFINED、FIELD 和 DISCRETE_FIELD。默认值为 UNIFORM。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

**返回值**

DisplacementBC 对象。

**异常**

无。

### 9.19.2 setValues(...)

此方法修改创建该对象的步骤中现有 DisplacementBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DisplacementBC](pt01ch09pyo19.md#ker-displacementbc-displacementbc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.19.3 setValuesInStep(...)

此方法修改指定步骤中现有 DisplacementBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*u1*

Float、Complex 或 SymbolicConstant，指定 1 方向的位移分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*u2*

Float、Complex 或 SymbolicConstant，指定 2 方向的位移分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*u3*

Float、Complex 或 SymbolicConstant，指定 3 方向的位移分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ur1*

Float、Complex 或 SymbolicConstant，指定关于 1 方向的旋转位移分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ur2*

Float、Complex 或 SymbolicConstant，指定关于 2 方向的旋转位移分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*ur3*

Float、Complex 或 SymbolicConstant，指定关于 3 方向的旋转位移分量。SymbolicConstant 的可能值为 SET、UNCHANGED 和 FREED。

*amplitude*

String 或 SymbolicConstant，指定幅值引用的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果幅值从前一个分析步骤传播，应使用 UNCHANGED。如果边界条件更改为没有幅值引用，应使用 FREED。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

**返回值**

无。

**异常**

无。

### 9.19.4 成员

DisplacementBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*distributionType*

SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM、USER_DEFINED、FIELD 和 DISCRETE_FIELD。默认值为 UNIFORM。

*fixed*

Boolean，指定边界条件是否应在步骤开始时保持在当前值。默认值为 OFF。

*buckleCase*

SymbolicConstant，指定边界条件在 [*BUCKLE](../key/key-link.md#usb-kws-hbuckle) 分析中的定义方式。可能的值为 NOT_APPLICABLE、STRESS_PERTURBATION、BUCKLING_MODES 和 PERTURBATION_AND_BUCKLING。默认值为 NOT_APPLICABLE。

*fieldName*

String，指定与此边界条件关联的 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称。*fieldName* 参数仅在 *distributionType*=FIELD 或 *distributionType*=DISCRETE_FIELD 时适用。默认值为空字符串。

*category*

SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
