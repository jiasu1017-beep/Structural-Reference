# 16.2 DisplayGroupInstance 对象

DisplayGroupInstance 对象存储在视口中显示的实体的 ID。DisplayGroupInstance 对象没有构造函数。当您设置要在视口中绘制的显示组时，Abaqus/CAE 为每个显示组创建一个 DisplayGroupInstance 对象，并将其放入 [DisplayGroupInstanceRepository](pt01ch16pyo03.md) 对象中。

**访问权限**

```
import assembly
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*]
import visualization
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*]
import part
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*]
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]
```

### 16.2.1 nodes()

此方法用于获取 DisplayGroupInstance 对象中存在的节点列表。它返回一个 Dictionary 对象，其键为部件实例名称，其值为属于该部件实例并包含在 DisplayGroupInstance 对象中的用户节点标签列表。此方法仅适用于作为 [OdbDisplay](pt01ch35pyo01.md) 对象的 DisplayGroupInstance 存储库成员的 DisplayGroupInstance 对象。

**参数**

无。

**返回值**

Dictionary 对象。

**异常**

无。

### 16.2.2 elements()

此方法返回 DisplayGroupInstance 对象中存在的元素列表。`elements` 方法返回一个 Dictionary 对象，使用部件实例名称作为键。Dictionary 对象中项的值是属于该部件实例并包含在 DisplayGroupInstance 对象中的用户元素标签列表。此方法仅适用于作为 [OdbDisplay](pt01ch35pyo01.md) 对象的 DisplayGroupInstance 存储库成员的 DisplayGroupInstance 对象。

**参数**

无。

**返回值**

Dictionary 对象。

**异常**

无。

### 16.2.3 setValues(...)

此方法修改 DisplayGroupInstance 对象。`setValues` 方法仅适用于作为 [OdbDisplay](pt01ch35pyo01.md) 对象的 DisplayGroupInstance 存储库成员的 DisplayGroupInstance 对象。

**必需参数**

无。

**可选参数**

*lockOptions*

布尔值，指定存储在 DisplayGroupInstance 对象上的显示选项是否应与视口显示选项的更改同步。此成员仅适用于作为 [OdbDisplay](pt01ch35pyo01.md) 对象的 DisplayGroupInstance 存储库成员的 DisplayGroupInstance 对象。默认值为 OFF。

**返回值**

无。

**异常**

无。

### 16.2.4 成员

DisplayGroupInstance 对象可以具有以下成员：

*name*

字符串，指定存储库键。

*lockOptions*

布尔值，指定存储在 DisplayGroupInstance 对象上的显示选项是否应与视口显示选项的更改同步。此成员仅适用于作为 [OdbDisplay](pt01ch35pyo01.md) 对象的 DisplayGroupInstance 存储库成员的 DisplayGroupInstance 对象。默认值为 OFF。

*odbDisplayOptions*

[OdbDisplayOptions](pt01ch40pyo18.md) 对象，指定此成员仅适用于作为 [OdbDisplay](pt01ch35pyo01.md) 对象的 DisplayGroupInstance 存储库成员的 DisplayGroupInstance 对象。

