# 10.2 Behavior 对象

Behavior 对象指定用于校准材料的方法。

**访问**

```
import calibration
mdb.models[*name*].calibrations[*name*].behaviors
```

### 10.2.1 Behavior(...)

此方法创建 Behavior 对象。

**路径**

```
mdb.models[*name*].calibrations[*name*].Behavior
```

**必需参数**

*name*

String，指定新行为的名称。

*typeName*

String，指定新 Behavior 的类型。值可以为"ElasIsoBehavior"、"ElasPlasIsoBehavior"、"FeFpBehavior"或用户插件行为类型。

**可选参数**

无。

**返回值**

Behavior 对象。

**异常**

InvalidNameError。

### 10.2.2 成员

Behavior 对象的成员与 [Behavior](pt01ch10pyo02.md#ker-behavior-behavior-pyc) 方法的参数具有相同的名称和描述。

此外，Behavior 对象可以具有以下成员：

*elasIsoBehavior*

[ElasIsoBehavior](pt01ch10pyo04.md) 对象。

*feFpBehavior*

[FeFpBehavior](pt01ch10pyo06.md) 对象。

*elasPlasIsoBehavior*

[ElasPlasIsoBehavior](pt01ch10pyo05.md) 对象。
