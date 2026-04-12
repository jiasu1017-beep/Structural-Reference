# 16.1 DisplayGroup 对象

DisplayGroup 对象用于选择视口中显示的实体子集。

**访问权限**

```
session.displayGroups[*name*]
import assembly
session.viewports[*name*].assemblyDisplay.displayGroup
session.viewports[*name*].layers[*name*].assemblyDisplay.displayGroup
import visualization
session.viewports[*name*].layers[*name*].odbDisplay.displayGroup
import part
session.viewports[*name*].layers[*name*].partDisplay.displayGroup
session.viewports[*name*].odbDisplay.displayGroup
session.viewports[*name*].partDisplay.displayGroup
```

### 16.1.1 DisplayGroup(...)

此方法创建一个 DisplayGroup 对象。

**路径**

```
session.DisplayGroup
```

**必需参数**

*name*

字符串，指定存储库键。

*leaf*

[Leaf](pt01ch16pyo04.md) 对象，指定显示组中的项。

**可选参数**

无。

**返回值**

DisplayGroup 对象。

**异常**

InvalidNameError。

### 16.1.2 add(...)

此方法将指定项添加到显示组。

**必需参数**

*leaf*

[Leaf](pt01ch16pyo04.md) 对象，指定要添加到显示组的项。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 16.1.3 either(...)

此方法重新定义显示组仅为 *leaf* 参数和显示组共有的那些项。

**必需参数**

*leaf*

[Leaf](pt01ch16pyo04.md) 对象，指定要从显示组中排除的项。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 16.1.4 intersect(...)

此方法重新定义显示组仅为 *leaf* 参数和显示组共有的那些项。

**必需参数**

*leaf*

[Leaf](pt01ch16pyo04.md) 对象，指定要包含在显示组中的项。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 16.1.5 redoLast()

此方法重做显示组上最后一个撤销的操作。

**参数**

无。

**返回值**

无。

**异常**

无。

### 16.1.6 remove(...)

此方法从显示组中移除指定项。

**必需参数**

*leaf*

[Leaf](pt01ch16pyo04.md) 对象，指定要从显示组中移除的项。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 16.1.7 replace(...)

此方法用指定项替换显示组的内容。

**必需参数**

*leaf*

[Leaf](pt01ch16pyo04.md) 对象，指定要替换当前显示组内容的项。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 16.1.8 undoLast()

此方法撤销对显示组执行的最后一个操作。

**参数**

无。

**返回值**

无。

**异常**

无。

### 16.1.9 成员

DisplayGroup 对象具有以下成员：

*canUndo*

布尔值，指定是否可以撤销。

*canRedo*

布尔值，指定是否可以重做。

*name*

字符串，指定存储库键。

*module*

符号常量，指定创建显示组的模块。可能的值为 PART、ASSEMBLY、PART_ASSEMBLY、ODB 和 ALL。

*modelName*

字符串，指定当模块基于部件或装配时，显示组所属模型的名称。

*partName*

字符串，指定当模块基于部件时，显示组所属部件的名称。

