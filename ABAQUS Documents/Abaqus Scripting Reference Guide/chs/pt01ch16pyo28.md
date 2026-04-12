# 16.28 LeafFromOdbNodePick 对象









LeafFromOdbNodePick 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromOdbNodePick 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupOdbToolset
```

### 16.28.1 LeafFromOdbNodePick(...)

此方法从包含机器可读的紧凑字符串的元组创建 [Leaf](pt01ch16pyo04.md) 对象，这些字符串定义每个部件实例拾取的节点。Leaf 对象指定显示组中的项目。

**路径**

```
LeafFromOdbNodePick
```

**必需参数**

*nodePick*

形式为 [部件名称、实体计数、机器可读拾取字符串] 的元组序列。

**可选参数**

无。

**返回值**

一个 LeafFromOdbNodePick 对象。

**异常**

无。

### 16.28.2 成员

LeafFromOdbNodePick 对象有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





