# 16.19 LeafFromNodeLabels 对象









LeafFromNodeLabels 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromNodeLabels 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupOdbToolset
```

### 16.19.1 LeafFromNodeLabels(...)

此方法从属于单个部件实例的节点标签序列创建 [Leaf](pt01ch16pyo04.md) 对象。

**路径**

```
LeafFromNodeLabels
```

**必需参数**

*partInstanceName*

一个 String，指定 *nodeLabels* 所引用的部件实例的名称。

*nodeLabels*

一个 String 序列，指定表示节点标签的表达式。表达式可以是以下任意一种：
- 一个 Int，指定单个节点标签；例如，`1`。
- 一个 String，指定单个节点标签；例如，`'7'`。
- 一个 String，指定节点标签序列；例如，`'3:5'` 和 `'3:15:3'`。

**可选参数**

无。

**返回值**

一个 LeafFromNodeLabels 对象。

**异常**

无。

### 16.19.2 成员

LeafFromNodeLabels 对象的成员与 [LeafFromNodeLabels](pt01ch16pyo19.md#ker-leaffromnodelabels-leaffromnodelabels-pyc) 方法的参数具有相同的名称和描述。

此外，LeafFromNodeLabels 对象还有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





