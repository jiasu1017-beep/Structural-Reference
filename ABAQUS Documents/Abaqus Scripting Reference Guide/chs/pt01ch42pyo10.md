# 42.10 KinematicHardening 对象

 KinematicHardening 对象存储初始等效塑性应变以及相关时的初始背应力张量的数据。

KinematicHardening 对象派生自 [PredefinedField](pt01ch42pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.10.1 KinematicHardening(...)

 此方法创建 KinematicHardening 对象。

**Path**

```
mdb.models[*name*].KinematicHardening
```

**必需参数**

*name*

 String，指定存储库键。

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

**可选参数**

*numBackStress*

 Int，指定背应力的数量。默认值为 1。

*equivPlasticStrain*

 Float 序列，指定初始等效塑性应变。

*backStress*

 Float 序列的序列，指定运动硬化模型的初始背应力张量。默认值为空序列。

*sectPtNum*

 Int 序列，指定截面点编号。此参数仅在 *definition*=SECTION_PTS 时有效。

*definition*

 SymbolicConstant，指定不同类型的运动硬化。可选值为 KINEMATIC_HARDENING、CRUSHABLE_FOAM、REBAR、SECTION_PTS 和 USER_DEFINED。默认值为 KINEMATIC_HARDENING。

*rebarLayerNames*

字符串序列，指定钢筋层名称。此参数仅在 *definition*=REBAR 时有效。

*distributionType*

 SymbolicConstant，指定负载是否均匀。可选值为 MAGNITUDE 和 ANALYTICAL_FIELD。默认值为 MAGNITUDE。

**返回值**

KinematicHardening 对象。

**异常**

无。

### 42.10.2 setValues(...)

此方法修改 KinematicHardening 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [KinematicHardening](pt01ch42pyo10.md#ker-kinematichardening-kinematichardening-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 42.10.3 成员

KinematicHardening 对象的成员与 [KinematicHardening](pt01ch42pyo10.md#ker-kinematichardening-kinematichardening-pyc) 方法的参数具有相同的名称和描述。

此外，KinematicHardening 对象可以具有以下成员：

*field*

 String，指定与此预定义场关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*field* 参数仅在 *distributionType*=ANALYTICAL_FIELD 时适用。默认值为空字符串。

### 42.10.4 对应分析关键字

| [*INITIAL CONDITIONS*](../key/key-link.md#usb-kws-minitialcond), TYPE=HARDENING |
| --- |

