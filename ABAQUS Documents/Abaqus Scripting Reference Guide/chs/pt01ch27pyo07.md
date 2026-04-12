# 27.7 BodyCurrentDensity 对象





BodyCurrentDensity 对象存储体电流的数据。

BodyCurrentDensity 对象派生自 [Load](pt01ch27pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.7.1 BodyCurrentDensity(...)

此方法创建 BodyCurrentDensity 对象。

**路径**

```
mdb.models[*name*].BodyCurrentDensity
```

**必需参数**

*name*

一个 String，指定载荷存储库密钥。

*createStepName*

一个 String，指定创建载荷的步骤名称。这必须是第一个分析步骤名称。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用载荷的区域。

*comp1*

一个 Complex，指定载荷的第一个分量。

*comp2*

一个 Complex，指定载荷的第二个分量。

*comp3*

一个 Complex，指定载荷的第三个分量。

**可选参数**

*amplitude*

一个 String 或 SymbolicConstant UNSET，指定幅值参考的名称。如果载荷没有幅值参考，应使用 UNSET。默认值为 UNSET。只有当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*distributionType*

一个 SymbolicConstant，指定载荷在空间上的分布方式。可能的值为 UNIFORM 和 USER_DEFINED。默认值为 UNIFORM。

**返回值**

一个 BodyCurrentDensity 对象。

**异常**

无。

### 27.7.2 setValues(...)

此方法修改创建载荷的步骤中现有 BodyCurrentDensity 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BodyCurrentDensity](pt01ch27pyo07.md#ker-bodycurrentdensity-bodycurrentdensity-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无

**异常**

无。

### 27.7.3 setValuesInStep(...)

此方法修改指定步骤中现有 BodyCurrentDensity 对象的传播数据。

**必需参数**

*stepName*

一个 String，指定修改载荷的步骤名称。

**可选参数**

*comp1*

一个 Complex，指定载荷的第一个分量。

*comp2*

一个 Complex，指定载荷的第二个分量。

*comp3*

一个 Complex，指定载荷的第三个分量。

*amplitude*

一个 String 或 SymbolicConstant，指定幅值参考的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果要从上一个静态分析步骤传播幅值，应使用 UNCHANGED。如果要将载荷更改为没有幅值参考，应使用 FREED。只有当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

无

**异常**

无。

### 27.7.4 成员

BodyCurrentDensity 对象可以具有以下成员：

*name*

一个 String，指定载荷存储库密钥。

*distributionType*

一个 SymbolicConstant，指定载荷在空间上的分布方式。可能的值为 UNIFORM 和 USER_DEFINED。默认值为 UNIFORM。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用载荷的区域。




