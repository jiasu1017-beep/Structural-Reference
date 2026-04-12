# 16.18 LeafFromModelNodeLabels 对象









LeafFromModelNodeLabels 对象可在需要 Leaf 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromModelNodeLabels 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupOdbToolset
```

### 16.18.1 LeafFromModelNodeLabels(...)

此方法从跨多个部件实例的节点标签序列创建 [Leaf](pt01ch16pyo04.md) 对象。

**路径**

```
LeafFromModelNodeLabels
```

**必需参数**

*nodeLabels*

一个 String 序列，指定模型中每个部件实例的节点标签表达式。每个部件实例节点表达式是一个 String（指定部件实例名称）和节点表达式序列的序列；例如，`(('partInstance1',(1,'7','3:15;3'),), ('partInstance2','8'),))`。节点表达式可以是以下任意一种：
- 一个 Int，指定单个节点标签；例如，`1`。
- 一个 String，指定单个节点标签；例如，`'7'`。
- 一个 String，指定节点标签序列；例如，`'3:5'` 和 `'3:15:3'`。

**可选参数**

无。

**返回值**

一个 LeafFromModelNodeLabels 对象。

**异常**

无。

### 16.18.2 成员

LeafFromModelNodeLabels 对象的成员与 [LeafFromModelNodeLabels](pt01ch16pyo18.md#ker-leaffrommodelnodelabels-leaffrommodelnodelabels-pyc) 方法的参数具有相同的名称和描述。

此外，LeafFromModelNodeLabels 对象还有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





