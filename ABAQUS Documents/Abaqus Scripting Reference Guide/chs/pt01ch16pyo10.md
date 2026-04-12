# 16.10 LeafFromGeometry 对象









LeafFromGeometry 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromGeometry 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupMdbToolset
```

### 16.10.1 LeafFromGeometry(...)

此方法从边缘、面和单元几何对象序列创建 Leaf 对象。允许边缘、面或单元参数的任意组合，但参数必须至少指定一个对象——不允许创建空叶子。

**路径**

```
LeafFromGeometry
```

**必需参数**

无。

**可选参数**

*edgeSeq*

几何边缘序列。

*faceSeq*

几何面序列。

*cellSeq*

几何单元序列。

**返回值**

一个 LeafFromGeometry 对象。

**异常**

如果未向此方法传递至少一个序列：

```
Cannot define empty leaf.
```

### 16.10.2 成员

LeafFromGeometry 对象有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





