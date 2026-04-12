# 42.3 FluidDensity 对象

FluidDensity 对象存储流体密度预定义场的数据。

FluidDensity 对象派生自 [PredefinedField](pt01ch42pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.3.1 FluidDensity(...)

此方法创建 FluidDensity 对象。

**Path**

```
mdb.models[*name*].FluidDensity
```

**必需参数**

*name*

 String，指定存储库键。

*createStepName*

 String，指定创建预定义场的步骤名称。

*region*

 Region，指定流体密度的域。使用 'None' 指定整个模型。

**可选参数**

*density*

 Float，指定流体密度。默认值为 0.0。

**返回值**

FluidDensity 对象。

**异常**

无。

### 42.3.2 setValues(...)

此方法修改 FluidDensity 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [FluidDensity](pt01ch42pyo03.md#ker-fluiddensity-fluiddensity-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无

**异常**

无。

### 42.3.3 成员

FluidDensity 对象可以具有以下成员：

*name*

 String，指定存储库键。

*density*

 Float，指定流体密度。默认值为 0.0。

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

### 42.3.4 对应分析关键字

| [*INITIAL CONDITIONS*](../key/key-link.md#usb-kws-minitialcond), TYPE=DENSITY |
| --- |

