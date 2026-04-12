# 42.9 InitialState 对象

InitialState 对象存储初始状态预定义场的数据。

InitialState 对象派生自 [PredefinedField](pt01ch42pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.9.1 InitialState(...)

此方法创建 InitialState 预定义场对象。

**Path**

```
mdb.models[*name*].InitialState
```

**必需参数**

*name*

 String，指定存储库键。

*instances*

 [PartInstanceArray](pt01ch06pyo04.md) 对象，指定应用预定义场的实例。

*fileName*

 String，指定生成初始状态数据的作业名称。

**可选参数**

*endStep*

 SymbolicConstant LAST_STEP 或 Int，指定要从中读取初始状态值的步骤，或 SymbolicConstant LAST_STEP。默认值为 LAST_STEP。

*endIncrement*

 SymbolicConstant STEP_END 或 Int，指定在 *endStep* 中设置的步骤的增量、间隔或迭代，或 SymbolicConstant STEP_END。默认值为 STEP_END。

*updateReferenceConfiguration*

 Boolean，指定是否根据导入数据更新参考配置。默认值为 OFF。

**返回值**

InitialState 对象。

**异常**

无。

### 42.9.2 setValues(...)

此方法修改 InitialState 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [InitialState](pt01ch42pyo09.md#ker-initialstate-initialstate-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 42.9.3 成员

InitialState 对象的成员与 [InitialState](pt01ch42pyo09.md#ker-initialstate-initialstate-pyc) 方法的参数具有相同的名称和描述。

此外，InitialState 对象可以具有以下成员：

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

### 42.9.4 对应分析关键字

| [*INSTANCE*](../key/key-link.md#usb-kws-minstance) |
| --- |

