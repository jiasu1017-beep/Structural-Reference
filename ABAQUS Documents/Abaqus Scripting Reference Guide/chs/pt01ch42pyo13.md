# 42.13 Temperature 对象

Temperature 对象存储温度预定义场的数据。

Temperature 对象派生自 [PredefinedField](pt01ch42pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.13.1 Temperature(...)

此方法创建 Temperature 对象。

**Path**

```
mdb.models[*name*].Temperature
```

**必需参数**

*name*

 String，指定存储库键。

*createStepName*

 String，指定创建预定义场的步骤名称。

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

**可选参数**

*distributionType*

 SymbolicConstant，指定预定义场如何空间变化。可选值为 UNIFORM、USER_DEFINED、FROM_FILE、FIELD、FROM_FILE_AND_USER_DEFINED 和 DISCRETE_FIELD。默认值为 UNIFORM。

*crossSectionDistribution*

 SymbolicConstant，指定预定义场如何分布在区域的截面上。可选值为
- CONSTANT_THROUGH_THICKNESS
- GRADIENTS_THROUGH_SHELL_CS
- GRADIENTS_THROUGH_BEAM_CS
- POINTS_THROUGH_SECTION

默认值为 CONSTANT_THROUGH_THICKNESS。

*field*

 String，指定与此预定义场关联的 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称。*field* 参数仅在 *distributionType*=FIELD 或 *distributionType*=DISCRETE_FIELD 时适用。默认值为空字符串。

*amplitude*

 String 或 SymbolicConstant UNSET，指定振幅引用名称。如果预定义场没有振幅引用，应使用 UNSET。默认值为 UNSET。

**注：** 仅当对指定步骤有效时，才应给出 *amplitude*。

*fileName*

 String，指定当 *distributionType*=FROM_FILE 或 *distributionType*=FROM_FILE_AND_USER_DEFINED 时要从中读取温度值的文件名。

*beginStep*

 Int，指定要从中读取温度值的第一步，或 SymbolicConstant FIRST_STEP 或 LAST_STEP。此参数仅在 *distributionType*=FROM_FILE 或 *distributionType*=FROM_FILE_AND_USER_DEFINED 时有效。默认值为 `None`。

*beginIncrement*

 Int，指定在 *beginStep* 中设置的步骤的第一步的增量，或 SymbolicConstants STEP_START 或 STEP_END。此参数仅在 *distributionType*=FROM_FILE 或 *distributionType*=FROM_FILE_AND_USER_DEFINED 时有效。默认值为 `None`。

*endStep*

 Int，指定要从中读取温度值的最后一步，或 SymbolicConstants FIRST_STEP 和 LAST_STEP。此参数仅在 *distributionType*=FROM_FILE 或 *distributionType*=FROM_FILE_AND_USER_DEFINED 时有效。默认值为 `None`。

*endIncrement*

 Int，指定在 *endStep* 中设置的步骤的最后一步的增量，或 SymbolicConstants STEP_START 和 STEP_END。此参数仅在 *distributionType*=FROM_FILE 或 *distributionType*=FROM_FILE_AND_USER_DEFINED 时有效。默认值为 `None`。

*interpolate*

 SymbolicConstant，指定是否对从输出数据库或结果文件读取的字段进行插值。可选值为 OFF、ON 或 MIDSIDE_ONLY。默认值为 OFF。

*magnitudes*

 Double 序列，指定当 *distributionType*=UNIFORM 或 FIELD 时的温度值。*magnitudes* 参数的值是 *crossSectionDistribution* 参数的函数，如下所列：
- 如果 *crossSectionDistribution*=CONSTANT_THROUGH_THICKNESS，则 *magnitudes* 是指定温度的 Double。
- 如果 *crossSectionDistribution*=GRADIENTS_THROUGH_SHELL_CS，则 *magnitudes* 是指定平均值和厚度方向梯度的 Double 序列。
- 如果 *crossSectionDistribution*=GRADIENTS_THROUGH_BEAM_CS，则 *magnitudes* 是指定平均值、N1 方向梯度和 N2 方向梯度的 Double 序列。
- 如果 *crossSectionDistribution*=POINTS_THROUGH_SECTION，则 *magnitudes* 是指定每个点的温度的 Double 序列。

*absoluteExteriorTolerance*

 Float，指定场的驱动节点可以位于全局模型元素区域外部的绝对值。默认值为 0.0。此参数不能与 *midside* 一起使用。

*exteriorTolerance*

 Float，指定场的驱动节点可以位于全局模型元素区域外部的平均元素大小的分数。默认值为 0.0。 此参数不能与 *midside* 一起使用。

**返回值**

Temperature 对象。

**异常**

无。

### 42.13.2 move(...)

此方法将 [TemperatureState](pt01ch42pyo14.md) 对象从一个步骤移动到不同的步骤。

**必需参数**

*fromStepName*

 String，指定从中移动 [PredefinedFieldState](pt01ch42pyo12.md) 的步骤名称。

*toStepName*

 String，指定将 [PredefinedFieldState](pt01ch42pyo12.md) 移动到的步骤名称。

**可选参数**

无。

**返回值**

无

**异常**

TextError。

### 42.13.3 setValues(...)

此方法修改步骤中现有 Temperature 对象的数据。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [Temperature](pt01ch42pyo13.md#ker-temperature-temperature-pyc) 方法的可选参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无

**异常**

无。

### 42.13.4 setValuesInStep(...)

此方法在指定步骤中修改现有 Temperature 对象的传播数据。

**必需参数**

*stepName*

 String，指定修改预定义场的步骤名称。

**可选参数**

 `setValuesInStep` 的可选参数与 [Temperature](pt01ch42pyo13.md#ker-temperature-temperature-pyc) 方法的可选参数相同，但 *distributionType* 和 *crossSectionDistribution* 参数除外。
无。

**返回值**

无

**异常**

无。

### 42.13.5 成员

Temperature 对象可以具有以下成员：

*name*

 String，指定存储库键。

*distributionType*

 SymbolicConstant，指定预定义场如何空间变化。可选值为 UNIFORM、USER_DEFINED、FROM_FILE、FIELD、FROM_FILE_AND_USER_DEFINED 和 DISCRETE_FIELD。默认值为 UNIFORM。

*field*

 String，指定与此预定义场关联的 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称。*field* 参数仅在 *distributionType*=FIELD 或 *distributionType*=DISCRETE_FIELD 时适用。默认值为空字符串。

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

### 42.13.6 对应分析关键字

| [*INITIAL CONDITIONS*](../key/key-link.md#usb-kws-minitialcond), TYPE=TEMPERATURE |
| --- |
| [*TEMPERATURE*](../key/key-link.md#usb-kws-htemperature) |

