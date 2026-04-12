# 16.5 LeafFromDatums 对象

LeafFromDatums 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromDatums 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问权限**

```
import displayGroupMdbToolset
```

### 16.5.1 LeafFromDatums(...)

此方法从 datum 对象序列创建 [Leaf](pt01ch16pyo04.md) 对象。Leaf 对象指定显示组中的项目。

**路径**

```
LeafFromDatums
```

**必需参数**

*datumSeq*

datum 对象序列。

**可选参数**

无。

**返回值**

LeafFromDatums 对象。

**异常**

无。

### 16.5.2 成员

LeafFromDatums 对象具有以下成员：

*leafType*

符号常量，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。

