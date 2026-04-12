# 45.1 Assembly 对象

以下命令对 Assembly 对象操作。有关 Assembly 对象的更多信息，请参阅["Assembly 对象，"第 6.1 节](pt01ch06pyo01.md)。

**访问**

```
import regionToolset
```

### 45.1.1 clashSets(...)

此命令打印描述两个集内容之间关系的信息。可能的 结果如下：
- 两个集相同。
- 集 2 是集 1 的子集。
- 集 2 是集 1 的超集。
- 集 2 与集 1 相交。
- 集 2 接触集 1（它们的边界相交）。
- 集 2 和集 1 不相交。

此命令仅接受位置参数，没有关键字。

**必需参数**

*arg1*

 Set 或 Surface 对象，指定集 1。

*arg2*

 Set 或 Surface 对象，指定集 2。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 45.1.2 deleteSets(...)

此命令从装配中删除给定的集。

**必需参数**

*setNames*

字符串序列，指定将从装配中删除的集名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 45.1.3 markSetInternal(...)

此命令将给定 Set 标记为内部或外部。

**必需参数**

*setName*

字符串，指定 Set 名称。

*internalSet*

 Boolean，指定 Set 是否应标记为内部。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 45.1.4 markSurfaceInternal(...)

此命令将给定 Surface 标记为内部或外部。

**必需参数**

*setName*

字符串，指定 Surface 名称。

*internalSurface*

 Boolean，指定 Surface 是否应标记为内部。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 45.1.5 isSetInternal(...)

此命令返回指示 Set 是否为内部的标志。

**必需参数**

*setName*

字符串，指定 Set 名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 45.1.6 isSurfaceInternal(...)

此命令返回指示 Surface 是否为内部的标志。

**必需参数**

*surfaceName*

字符串，指定 Surface 名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 45.1.7 deleteSurfaces(...)

此命令从装配中删除给定的曲面。

**必需参数**

*surfaceNames*

字符串序列，指定将从装配中删除的曲面名称。

**可选参数**

无。

**返回值**

无

**异常**

无。

