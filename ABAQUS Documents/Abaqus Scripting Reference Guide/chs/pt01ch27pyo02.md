# 27.2 BodyCharge 对象

BodyCharge 对象存储体电荷的数据。

BodyCharge 对象派生自 [Load](pt01ch27pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].loads[*name*]
```

### 27.2.1 BodyCharge(...)

此方法创建 BodyCharge 对象。

**路径**

```
mdb.models[*name*].BodyCharge
```

**必需参数**

*name*

String，指定载荷存储库密钥。

*createStepName*

String，指定要创建载荷的步骤名称。这必须是第一个分析步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定要施加载荷的区域。

*magnitude*

Float，指定载荷大小。

**可选参数**

*amplitude*

String 或 SymbolicConstant UNSET，指定幅值参考的名称。如果载荷没有幅值参考，应使用 UNSET。默认值为 UNSET。您应仅在步骤参数有效时提供 *amplitude* 参数。

*distributionType*

SymbolicConstant，指定载荷在空间上的分布方式。可能的值为 UNIFORM 和 FIELD。默认值为 UNIFORM。

*field*

String，指定与此载荷关联的 [AnalyticalField](pt01ch21pyo02.md) 对象名称。*field* 参数仅在 *distributionType*=FIELD 时适用。默认值为空字符串。

**返回值**

BodyCharge 对象。

**异常**

无。

### 27.2.2 setValues(...)

此方法修改在创建载荷的步骤中现有 BodyCharge 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BodyCharge](pt01ch27pyo02.md#ker-bodycharge-bodycharge-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 27.2.3 setValuesInStep(...)

此方法修改在指定步骤中现有 BodyCharge 对象的传播数据。

**必需参数**

*stepName*

String，指定要修改载荷的步骤名称。

**可选参数**

*magnitude*

Float，指定载荷大小。

*amplitude*

String 或 SymbolicConstant，指定幅值参考的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果要从先前的静态分析步骤传播幅值，应使用 UNCHANGED。如果要将载荷改为没有幅值参考，应使用 FREED。您应仅在步骤参数有效时提供 *amplitude* 参数。

**返回值**

无。

**异常**

无。

### 27.2.4 成员

BodyCharge 对象可以具有以下成员：

*name*

String，指定载荷存储库密钥。

*distributionType*

SymbolicConstant，指定载荷在空间上的分布方式。可能的值为 UNIFORM 和 FIELD。默认值为 UNIFORM。

*field*

String，指定与此载荷关联的 [AnalyticalField](pt01ch21pyo02.md) 对象名称。*field* 参数仅在 *distributionType*=FIELD 时适用。默认值为空字符串。

*region*

[Region](pt01ch45pyo03.md) 对象，指定要施加载荷的区域。
