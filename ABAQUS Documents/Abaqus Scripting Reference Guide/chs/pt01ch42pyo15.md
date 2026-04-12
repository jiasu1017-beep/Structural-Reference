# 42.15 Velocity 对象

Velocity 对象存储初始速度预定义场的数据。

Velocity 对象派生自 [PredefinedField](pt01ch42pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.15.1 Velocity(...)

此方法创建 Velocity 预定义场对象。

**Path**

```
mdb.models[*name*].Velocity
```

**必需参数**

*name*

 String，指定存储库键。

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

*velocity1*

 Float，指定速度的第一个分量。

*velocity2*

 Float，指定速度的第二个分量。

*velocity3*

 Float，指定速度的第三个分量。

*omega*

 Float，指定角速度。

*axisBegin*

 Float 序列，指定 *omega* 所绕轴的起点的 *X-*、*Y-* 和 *Z-* 坐标。

*axisEnd*

 Float 序列，指定 *omega* 所绕轴的终点的 *X-*、*Y-* 和 *Z-* 坐标。

**可选参数**

*field*

 String，指定与此预定义场关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*field* 参数仅在 *distributionType*=FIELD_ANALYTICAL 时适用。默认值为空字符串。

*distributionType*

 SymbolicConstant，指定负载是否均匀。可选值为 MAGNITUDE 和 FIELD_ANALYTICAL。默认值为 MAGNITUDE。

**返回值**

Velocity 对象。

**异常**

无。

### 42.15.2 setValues(...)

此方法修改 Velocity 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [Velocity](pt01ch42pyo15.md#ker-velocity-velocity-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 42.15.3 成员

Velocity 对象的成员与 [Velocity](pt01ch42pyo15.md#ker-velocity-velocity-pyc) 方法的参数具有相同的名称和描述。

### 42.15.4 对应分析关键字

| [*INITIAL CONDITIONS*](../key/key-link.md#usb-kws-minitialcond), TYPE=VELOCITY |
| --- |
| [*INITIAL CONDITIONS*](../key/key-link.md#usb-kws-minitialcond), TYPE=ROTATING VELOCITY |

