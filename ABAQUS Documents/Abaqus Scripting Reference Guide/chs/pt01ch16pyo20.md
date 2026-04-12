# 16.20 LeafFromNodeSets 对象









LeafFromNodeSets 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromNodeSets 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupOdbToolset
```

### 16.20.1 LeafFromNodeSets(...)

此方法从节点集序列创建 [Leaf](pt01ch16pyo04.md) 对象。

**路径**

```
LeafFromNodeSets
```

**必需参数**

*nodeSets*

一个 String 序列，指定节点集；或一个 String，指定单个节点集。

**可选参数**

无。

**返回值**

一个 LeafFromNodeSets 对象。

**异常**

无。

### 16.20.2 成员

LeafFromNodeSets 对象的成员与 [LeafFromNodeSets](pt01ch16pyo20.md#ker-leaffromnodesets-leaffromnodesets-pyc) 方法的参数具有相同的名称和描述。

此外，LeafFromNodeSets 对象还有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





