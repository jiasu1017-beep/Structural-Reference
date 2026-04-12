# 16.31 LeafFromPartNodeLabels 对象









LeafFromPartNodeLabels 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromPartNodeLabels 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupMdbToolset
```

### 16.31.1 LeafFromPartNodeLabels(...)

此方法从指定节点标签的 String 序列创建 [Leaf](pt01ch16pyo04.md) 对象。Leaf 对象指定显示组中的项目。

**路径**

```
LeafFromPartNodeLabels
```

**必需参数**

*part*

一个 [Part](pt01ch37pyo01.md) 对象。

*nodeLabels*

一个 String 序列，指定节点标签。

**可选参数**

无。

**返回值**

一个 LeafFromPartNodeLabels 对象。

**异常**

无。

### 16.31.2 成员

LeafFromPartNodeLabels 对象有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





