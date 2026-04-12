# 42.5 FluidTurbulence 对象

FluidTurbulence 对象存储流体湍流预定义场的数据。此预定义场仅在流步骤中选择了湍流模型时适用。

FluidTurbulence 对象派生自 [PredefinedField](pt01ch42pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.5.1 FluidTurbulence(...)

此方法创建 FluidTurbulence 对象。

**Path**

```
mdb.models[*name*].FluidTurbulence
```

**必需参数**

*name*

 String，指定存储库键。

*createStepName*

 String，指定创建预定义场的步骤名称。

*region*

 Region，指定流体湍流的域。使用 'None' 指定整个模型。

**可选参数**

*eddyViscosity*

 Float，指定流体湍流的涡粘度。此参数仅在流步骤中选择了 Spalart-Allmaras 湍流模型时适用。默认值为 0.0。

*dissipationRate*

 Float，指定流体湍流的耗散率。此参数仅在流步骤中选择了 k-epsilon 归一化群 (RNG) 湍流模型时适用。默认值为 0.0。

*turbulentKE*

 Float，指定流体湍流的动能。此参数仅在流步骤中选择了 k-epsilon 归一化群 (RNG) 湍流模型时适用。默认值为 0.0。

**返回值**

FluidTurbulence 对象。

**异常**

无。

### 42.5.2 setValues(...)

此方法修改 FluidTurbulence 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [FluidTurbulence](pt01ch42pyo05.md#ker-fluidturbulence-fluidturbulence-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无

**异常**

无。

### 42.5.3 成员

FluidTurbulence 对象可以具有以下成员：

*name*

 String，指定存储库键。

*eddyViscosity*

 Float，指定流体湍流的涡粘度。此参数仅在流步骤中选择了 Spalart-Allmaras 湍流模型时适用。默认值为 0.0。

*dissipationRate*

 Float，指定流体湍流的耗散率。此参数仅在流步骤中选择了 k-epsilon 归一化群 (RNG) 湍流模型时适用。默认值为 0.0。

*turbulentKE*

 Float，指定流体湍流的动能。此参数仅在流步骤中选择了 k-epsilon 归一化群 (RNG) 湍流模型时适用。默认值为 0.0。

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

### 42.5.4 对应分析关键字

| [*INITIAL CONDITIONS*](../key/key-link.md#usb-kws-minitialcond), TYPE=TURBNU, TYPE=TURBKE, TYPE= TURBEPS, ELEMENT AVERAGE |
| --- |

