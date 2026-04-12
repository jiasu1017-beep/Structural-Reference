# 25.62 SelfContactStd 对象

SelfContactStd 对象在 Abaqus/Standard 分析期间定义自接触。

SelfContactStd 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.62.1 SelfContactStd(...)

此方法创建一个 SelfContactStd 对象。

**路径**

```
mdb.models[*name*].SelfContactStd
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 SelfContactStd 对象的步骤名称。

*surface*

[Region](pt01ch45pyo03.md) 对象，指定定义自接触的表面。

*interactionProperty*

字符串，指定与此交互关联的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。

**可选参数**

*enforcement*

 SymbolicConstant，指定离散化方法。可能的值为 NODE_TO_SURFACE 和 SURFACE_TO_SURFACE。默认值为 SURFACE_TO_SURFACE。

*thickness*

布尔值，指定是否考虑壳/膜元素厚度。默认值为 ON。

此参数仅在 *enforcement*=SURFACE_TO_SURFACE 时有效。

*smooth*

浮点数，指定当 *enforcement*=NODE_TO_SURFACE 时涉及的变形或刚性主表面使用的平滑程度。值必须在 0.0 和 0.5 之间。默认值为 0.2。

*contactControls*

字符串，指定与此交互关联的 [ContactControl](pt01ch25pyo16.md) 对象的名称。空字符串表示将使用默认接触控制。默认值为空字符串。

**返回值**

SelfContactStd 对象。

**异常**

无。

### 25.62.2 setValues(...)

此方法修改创建 SelfContactStd 对象的步骤中现有 SelfContactStd 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SelfContactStd](pt01ch25pyo62.md#ker-selfcontactstd-selfcontactstd-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.62.3 setValuesInStep(...)

此方法修改指定步骤中现有 SelfContactStd 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

*interactionProperty*

字符串，指定与此交互关联的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。

*contactControls*

字符串，指定与此交互关联的 [ContactControl](pt01ch25pyo16.md) 对象的名称。空字符串表示将使用默认接触控制。默认值为空字符串。

**返回值**

无。

**异常**

无。

### 25.62.4 成员

SelfContactStd 对象的成员与 [SelfContactStd](pt01ch25pyo62.md#ker-selfcontactstd-selfcontactstd-pyc) 方法的参数具有相同的名称和描述。

此外，SelfContactStd 对象具有以下成员：

*contactTracking*

 SymbolicConstant，指定接触跟踪算法的选择。STATE 跟踪算法仅使用法向投影，通过使用 ONE_CONFIG 指定。PATH 跟踪算法使用交叉和法向投影，通过使用 TWO_CONFIG 指定。可能的值为 ONE_CONFIG 和 TWO_CONFIG。默认值为 TWO_CONFIG。

此参数仅在 *enforcement*=SUR