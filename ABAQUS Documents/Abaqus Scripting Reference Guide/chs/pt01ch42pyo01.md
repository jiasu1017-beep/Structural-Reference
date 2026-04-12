# 42.1 PredefinedField 对象

PredefinedField 对象是 `predefined field` 存储库中对象的基对象。PredefinedField 对象的方法和成员对从 PredefinedField 派生的所有对象通用。

任何 PredefinedField 对象的实例都可以通过 [Model](pt01ch33pyo01.md) 对象的 `predefined field` 存储库获得。任何 PredefinedFieldState 对象的实例都可以通过 [Step](pt01ch49pyo01.md) 对象的 `predefined field` 存储库获得。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.1.1 move(...)

此方法将特定 [PredefinedFieldState](pt01ch42pyo12.md) 对象从一个步骤移动到不同的步骤。

**必需参数**

*fromStepName*

 String，指定从中移动 [PredefinedFieldState](pt01ch42pyo12.md) 对象的步骤名称。

*toStepName*

 String，指定将 [PredefinedFieldState](pt01ch42pyo12.md) 对象移动到的步骤名称。

**可选参数**

无。

**返回值**

无

**异常**

TextError。

### 42.1.2 resume()

此方法恢复先前被抑制的预定义场。

**参数**

无。

**返回值**

无

**异常**

无。

### 42.1.3 suppress()

此方法抑制预定义场。

**参数**

无。

**返回值**

无

**异常**

无。

### 42.1.4 delete(...)

 此方法允许您删除现有字段。

**必需参数**

*indices*

 Int 序列，指定每个要删除的字段的索引。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 42.1.5 成员

PredefinedField 对象可以具有以下成员：

*name*

 String，指定存储库键。

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

