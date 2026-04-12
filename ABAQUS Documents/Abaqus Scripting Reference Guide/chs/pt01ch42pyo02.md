# 42.2 FluidCavityPressure 对象

FluidCavityPressure 对象存储初始流体腔压力的数据。基本类*region* 参数不能与此对象一起指定。

FluidCavityPressure 对象派生自 [PredefinedField](pt01ch42pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.2.1 FluidCavityPressure(...)

此方法创建 FluidCavityPressure 对象。

**Path**

```
mdb.models[*name*].FluidCavityPressure
```

**必需参数**

*name*

 String，指定存储库键。

*fluidCavity*

 String，指定流体腔相互作用的名称。

*fluidPressure*

 Float，指定初始流体压力。

**可选参数**

无。

**返回值**

FluidCavityPressure 对象。

**异常**

无。

### 42.2.2 setValues(...)

此方法修改 FluidCavityPressure 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [FluidCavityPressure](pt01ch42pyo02.md#ker-fluidcavitypressure-fluidcavitypressure-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 42.2.3 成员

FluidCavityPressure 对象的成员与 [FluidCavityPressure](pt01ch42pyo02.md#ker-fluidcavitypressure-fluidcavitypressure-pyc) 方法的参数具有相同的名称和描述。

此外，FluidCavityPressure 对象可以具有以下成员：

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

### 42.2.4 对应分析关键字

| [*INITIAL CONDITIONS*](../key/key-link.md#usb-kws-minitialcond), TYPE=FLUID PRESSURE |
| --- |

