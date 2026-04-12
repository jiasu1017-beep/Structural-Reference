# 16.3 DisplayGroupInstanceRepository 对象

DisplayGroupInstanceRepository 对象存储 [DisplayGroupInstance](pt01ch16pyo02.md) 对象。除了所有标准 Python 存储库方法外，[DisplayGroupInstance](pt01ch16pyo02.md) 存储库还定义了下述附加方法。

**访问权限**

```
import visualization
session.viewports[*name*].layers[*name*].odbDisplay.displayGroupInstances
session.viewports[*name*].odbDisplay.displayGroupInstances
```

### 16.3.1 syncOptions(...)

此方法将存储在 [OdbDisplay](pt01ch35pyo01.md) 对象上的显示选项与存储在 [DisplayGroupInstance](pt01ch16pyo02.md) 对象上的显示选项同步。

**必需参数**

*name*

字符串，指定存储库键。

**可选参数**

*updateInstances*

布尔值，指定是否为 DisplayGroupInstanceRepository 中存储的所有 *lockOptions* 为 OFF 的 [DisplayGroupInstance](pt01ch16pyo02.md) 对象同步显示选项。*updateInstances* 的默认值为 ON。

**返回值**

无。

**异常**

无。

### 16.3.2 成员

DisplayGroupInstanceRepository 对象没有成员。

