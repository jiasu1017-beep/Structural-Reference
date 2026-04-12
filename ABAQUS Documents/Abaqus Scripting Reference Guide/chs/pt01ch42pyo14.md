# 42.14 TemperatureState 对象

TemperatureState 对象存储步骤中温度的传播数据。此对象的一个实例由 [Temperature](pt01ch42pyo13.md) 对象为每个步骤内部创建。

TemperatureState 对象没有构造函数或方法。

TemperatureState 对象派生自 [PredefinedFieldState](pt01ch42pyo12.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].predefinedFieldStates[*name*]
```

### 42.14.1 成员

TemperatureState 对象可以具有以下成员：

*fileNameState*

 SymbolicConstant，指定 *fileName* 成员的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*beginStep*

 SymbolicConstant 或 Int，指定要从中读取温度值的第一步。此参数仅在 *distribution*=FROM_FILE 或 *distribution*=FROM_FILE_AND_USER_DEFINED 时有效。可选值为 FIRST_STEP、LAST_STEP 和 NONE。默认值为 NONE。

*beginStepState*

 SymbolicConstant，指定 *beginStep* 成员的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*beginIncrement*

 `None` 或 Int，指定在 *beginStep* 中设置的步骤的第一步的增量，或 SymbolicConstants STEP_START 或 STEP_END。此参数仅在 *distributionType*=FROM_FILE 或 *distributionType*=FROM_FILE_AND_USER_DEFINED 时有效。默认值为 `None`。

*beginIncrementState*

 SymbolicConstant，指定 *beginIncrement* 成员的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*endStep*

 `None` 或 Int，指定要从中读取温度值的最后一步，或 SymbolicConstants FIRST_STEP 和 LAST_STEP。此参数仅在 *distributionType*=FROM_FILE 或 *distributionType*=FROM_FILE_AND_USER_DEFINED 时有效。默认值为 `None`。

*endStepState*

 SymbolicConstant，指定 *endStep* 成员的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*endIncrement*

 `None` 或 Int，指定在 *endStep* 中设置的步骤的最后一步的增量，或 SymbolicConstants STEP_START 和 STEP_END。此参数仅在 *distributionType*=FROM_FILE 或 *distributionType*=FROM_FILE_AND_USER_DEFINED 时有效。默认值为 `None`。

*endIncrementState*

 SymbolicConstant，指定 *endIncrement* 成员的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*midside*

 Boolean，指定是否从角节点温度对二阶元素中的温度进行插值。此参数仅在 *distributionType*=FROM_FILE 或 *distributionType*=FROM_FILE_AND_USER_DEFINED 时有效。

*midsideState*

 SymbolicConstant，指定 *midside* 成员的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*amplitudeState*

 SymbolicConstant，指定 *amplitudeState* 成员的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*fileName*

 String，指定当 *distributionType*=FROM_FILE 或 *distributionType*=FROM_FILE_AND_USER_DEFINED 时要从中读取温度值的文件名。

*amplitude*

 SymbolicConstant UNSET 或 String，指定振幅引用名称。如果预定义场没有振幅引用，应使用 SymbolicConstant UNSET。默认值为 UNSET。

**注：** 仅当对指定步骤有效时，才应给出 *amplitude*。

*magnitudesState*

 SymbolicConstant 元组，指定 *magnitudes* 成员每个项目的传播状态。可选值为 UNSET、SET 和 UNCHANGED。

*magnitudes*

 Float 元组，指定当 *distributionType*=UNIFORM 或 *distributionType*=FIELD 时的温度值。*magnitudes* 参数的值是 *crossSectionDistribution* 参数的函数，如下所列：
- 如果 *crossSectionDistribution*=CONSTANT_THROUGH_THICKNESS，则 *magnitudes* 是指定温度的 Double。
- 如果 *crossSectionDistribution*=GRADIENTS_THROUGH_SHELL_CS，则 *magnitudes* 是指定平均值和厚度方向梯度的 Double 序列。
- 如果 *crossSectionDistribution*=GRADIENTS_THROUGH_BEAM_CS，则 *magnitudes* 是指定平均值、N1 方向梯度和 N2 方向梯度的 Double 序列。
- 如果 *crossSectionDistribution*=POINTS_THROUGH_SECTION，则 *magnitudes* 是指定每个点的温度的 Double 序列。

*status*

 SymbolicConstant，指定 [PredefinedFieldState](pt01ch42pyo12.md) 对象的传播状态。可选值为：
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- DEACTIVATED_TO_INITIAL
- NO_LONGER_ACTIVE
- RESET_TO_INITIAL
- TO_BE_COMPUTED
- PROPAGATED_FROM_COMPUTED
- BUILT_INTO_BASE_STATE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE

此成员存在于所有 [PredefinedFieldState](pt01ch42pyo12.md) 对象中，但不同的预定义场根据传播规则使用整个可能值列表的不同子集。

