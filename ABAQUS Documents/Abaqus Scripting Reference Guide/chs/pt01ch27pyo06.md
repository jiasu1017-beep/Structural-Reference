# 27.6 BodyCurrent 对象





BodyCurrent 对象存储体电流的数据。

BodyCurrent 对象派生自 [Load](pt01ch27pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.6.1 BodyCurrent(...)

此方法创建 BodyCurrent 对象。

**路径**

```
mdb.models[*name*].BodyCurrent
```

**必需参数**

*name*

一个 String，指定载荷存储库密钥。

*createStepName*

一个 String，指定创建载荷的步骤名称。这必须是第一个分析步骤名称。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用载荷的区域。

*magnitude*

一个 Float，指定载荷大小。

**可选参数**

*amplitude*

一个 String 或 SymbolicConstant UNSET，指定幅值参考的名称。如果载荷没有幅值参考，应使用 UNSET。默认值为 UNSET。只有当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*distributionType*

一个 SymbolicConstant，指定载荷在空间上的分布方式。可能的值为 UNIFORM 和 FIELD。默认值为 UNIFORM。

*field*

一个 String，指定与该载荷关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*field* 参数仅在 *distributionType*=FIELD 时适用。默认值为空字符串。

**返回值**

一个 BodyCurrent 对象。

**异常**

无。

### 27.6.2 setValues(...)

此方法修改创建载荷的步骤中现有 BodyCurrent 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BodyCurrent](pt01ch27pyo06.md#ker-bodycurrent-bodycurrent-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无

**异常**

无。

### 27.6.3 setValuesInStep(...)

此方法修改指定步骤中现有 BodyCurrent 对象的传播数据。

**必需参数**

*stepName*

一个 String，指定修改载荷的步骤名称。

**可选参数**

*magnitude*

一个 Float，指定载荷大小。

*amplitude*

一个 String 或 SymbolicConstant，指定幅值参考的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果要从上一个静态分析步骤传播幅值，应使用 UNCHANGED。如果要将载荷更改为没有幅值参考，应使用 FREED。只有当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

无

**异常**

无。

### 27.6.4 成员

BodyCurrent 对象可以具有以下成员：

*name*

一个 String，指定载荷存储库密钥。

*distributionType*

一个 SymbolicConstant，指定载荷在空间上的分布方式。可能的值为 UNIFORM 和 FIELD。默认值为 UNIFORM。

*field*

一个 String，指定与该载荷关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*field* 参数仅在 *distributionType*=FIELD 时适用。默认值为空字符串。

*region*

一个 [Region](pt01ch45pyo03.md) 对象，指定应用载荷的区域。




