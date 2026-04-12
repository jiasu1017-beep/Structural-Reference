# 25.60 SelfContactExp 对象

SelfContactExp 对象在 Abaqus/Explicit 分析期间定义自接触。

SelfContactExp 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.60.1 SelfContactExp(...)

此方法创建一个 SelfContactExp 对象。

**路径**

```
mdb.models[*name*].SelfContactExp
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 SelfContactExp 对象的步骤名称。

*surface*

[Region](pt01ch45pyo03.md) 对象，指定定义自接触的表面。

*interactionProperty*

字符串，指定与此交互关联的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。

**可选参数**

*mechanicalConstraint*

 SymbolicConstant，指定机械约束公式。可能的值为 KINEMATIC 和 PENALTY。默认值为 KINEMATIC。

*contactControls*

字符串，指定与此交互关联的 [ContactControl](pt01ch25pyo16.md) 对象的名称。空字符串表示将使用默认接触控制。默认值为空字符串。

**返回值**

SelfContactExp 对象。

**异常**

无。

### 25.60.2 setValues(...)

此方法修改创建 SelfContactExp 对象的步骤中现有 SelfContactExp 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SelfContactExp](pt01ch25pyo60.md#ker-selfcontactexp-selfcontactexp-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.60.3 setValuesInStep(...)

此方法修改指定步骤中现有 SelfContactExp 对象的传播数据。

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

### 25.60.4 成员

SelfContactExp 对象的成员与 [SelfContactExp](