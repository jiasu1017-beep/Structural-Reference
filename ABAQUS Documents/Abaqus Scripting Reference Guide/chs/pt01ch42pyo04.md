# 42.4 FluidThermalEnergy 对象

FluidThermalEnergy 对象存储流体热能预定义场的数据。此预定义场仅在流步骤中选择了能量方程时适用。

FluidThermalEnergy 对象派生自 [PredefinedField](pt01ch42pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.4.1 FluidThermalEnergy(...)

此方法创建 FluidThermalEnergy 对象。

**Path**

```
mdb.models[*name*].FluidThermalEnergy
```

**必需参数**

*name*

 String，指定存储库键。

*createStepName*

 String，指定创建预定义场的步骤名称。

*region*

 Region，指定流体热能的域。使用 'None' 指定整个模型。

**可选参数**

*temperature*

 Float，指定流体温度。默认值为 0.0。

*distributionType*

 SymbolicConstant，指定负载是否均匀。可选值为 MAGNITUDE、ANALYTICAL_FIELD 和 DISCRETE_FIELD。默认值为 MAGNITUDE。

**返回值**

FluidThermalEnergy 对象。

**异常**

无。

### 42.4.2 setValues(...)

此方法修改 FluidThermalEnergy 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [FluidThermalEnergy](pt01ch42pyo04.md#ker-fluidthermalenergy-fluidthermalenergy-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无

**异常**

无。

### 42.4.3 成员

FluidThermalEnergy 对象可以具有以下成员：

*name*

 String，指定存储库键。

*temperature*

 Float，指定流体温度。默认值为 0.0。

*distributionType*

 SymbolicConstant，指定负载是否均匀。可选值为 MAGNITUDE、ANALYTICAL_FIELD 和 DISCRETE_FIELD。默认值为 MAGNITUDE。

*field*

 String，指定与此预定义场关联的 [AnalyticalField](pt01ch21pyo02.md) 对象的名称。*field* 参数仅在 *distributionType*=ANALYTICAL_FIELD 时适用。默认值为空字符串。

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

### 42.4.4 对应分析关键字

| [*INITIAL CONDITIONS*](../key/key-link.md#usb-kws-minitialcond), TYPE=TEMPERATURE, ELEMENT AVERAGE |
| --- |

