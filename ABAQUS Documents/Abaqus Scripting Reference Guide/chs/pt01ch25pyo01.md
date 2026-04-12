# 25.1 Interaction 对象





Interaction 对象是其他 Interaction 对象的抽象基类型。Interaction 对象没有显式构造函数。每个 Interaction 对象具有以下方法：
- `deactivate`
- `move`
- `reset`
- `resume`
- `suppress`
- `delete`

这些方法如下所述。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.1.1 deactivate(...)

此方法在指定步骤及其所有后续步骤中停用交互。

**必需参数**

*stepName*

一个 String，指定停用交互的步骤名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 25.1.2 move(...)

此方法将交互从一个步骤移动到另一个步骤。

**必需参数**

*fromStepName*

一个 String，指定要移动交互的起始步骤名称。

*toStepName*

一个 String，指定要移动交互的目标步骤名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 25.1.3 reset(...)

此方法重新激活先前停用的交互。`reset` 方法在最初停用交互的步骤中可用。

**必需参数**

*stepName*

一个 String，指定重新激活交互的步骤名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 25.1.4 resume()

此方法恢复先前被抑制的交互。

**参数**

无。

**返回值**

无

**异常**

无。

### 25.1.5 suppress()

此方法抑制交互。

**参数**

无。

**返回值**

无

**异常**

无。

### 25.1.6 delete(...)

此方法允许您删除现有的交互。

**必需参数**

*indices*

一个 Int 序列，指定要删除的每个交互的索引。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 25.1.7 成员

Interaction 对象具有以下成员：

*name*

一个 String，指定存储库键。





