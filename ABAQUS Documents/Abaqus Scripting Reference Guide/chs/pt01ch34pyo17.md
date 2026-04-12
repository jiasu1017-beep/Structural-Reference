# 34.16 OdbLoadCase 对象

OdbLoadCase 对象描述一个负载情况。

**访问**

```
import odbAccess
session.odbs[*name*].steps[*name*].frames[*i*].loadCase
session.odbs[*name*].steps[*name*].historyRegions[*name*].loadCase
session.odbs[*name*].steps[*name*].loadCases[*name*]
```

### 34.16.1 LoadCase(...)

此方法创建 OdbLoadCase 对象。

**路径**

```
session.odbs[*name*].steps[*name*].LoadCase
```

**必要参数**

*name*

一个字符串，指定 OdbLoadCase 对象的名称。

**可选参数**

无。

**返回值**

OdbLoadCase 对象。

**异常**

无。

### 34.16.2 成员

OdbLoadCase 对象具有与 [LoadCase](pt01ch34pyo16.md#ker-odbloadcase-loadcase-pyc) 方法的参数名称和描述相同的成员。
