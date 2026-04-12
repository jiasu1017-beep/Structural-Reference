# 42.6 FluidVelocity 对象

FluidVelocity 对象存储流体速度预定义场的数据。

FluidVelocity 对象派生自 [PredefinedField](pt01ch42pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.6.1 FluidVelocity(...)

此方法创建 FluidVelocity 对象。

**Path**

```
mdb.models[*name*].FluidVelocity
```

**必需参数**

*name*

 String，指定存储库键。

*createStepName*

 String，指定创建预定义场的步骤名称。

*region*

 Region，指定流体速度的域。使用 'None' 指定整个模型。

**可选参数**

*velocity1*

 Float，指定 1 方向上的流体速度。默认值为 0.0。

*velocity2*

 Float，指定 2 方向上的流体速度。默认值为 0.0。

*velocity3*

 Float，指定 3 方向上的流体速度。默认值为 0.0。

**返回值**

FluidVelocity 对象。

**异常**

无。

### 42.6.2 setValues(...)

此方法修改 FluidVelocity 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [FluidVelocity](pt01ch42pyo06.md#ker-fluidvelocity-fluidvelocity-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无

**异常**

无。

### 42.6.3 成员

FluidVelocity 对象可以具有以下成员：

*name*

 String，指定存储库键。

*velocity1*

 Float，指定 1 方向上的流体速度。默认值为 0.0。

*velocity2*

 Float，指定 2 方向上的流体速度。默认值为 0.0。

*velocity3*

 Float，指定 3 方向上的流体速度。默认值为 0.0。

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

### 42.6.4 对应分析关键字

| [*INITIAL CONDITIONS*](../key/key-link.md#usb-kws-minitialcond), TYPE=VELOCITY, ELEMENT AVERAGE |
| --- |

