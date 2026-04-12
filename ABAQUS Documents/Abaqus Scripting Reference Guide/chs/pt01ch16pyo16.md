# 16.17 LeafFromModelElemLabels 对象









LeafFromModelElemLabels 对象可在需要 Leaf 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromModelElemLabels 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupOdbToolset
```

### 16.17.1 LeafFromModelElemLabels(...)

此方法从跨多个部件实例的元素标签序列创建 [Leaf](pt01ch16pyo04.md) 对象。

**路径**

```
LeafFromModelElemLabels
```

**必需参数**

*elementLabels*

一个 String 序列，指定模型中每个部件实例的元素标签表达式。每个部件实例元素表达式是一个 String（指定部件实例名称）和元素表达式序列的序列；例如，`(('partInstance1',(1,'7','3:15;3'),), ('partInstance2','8'),))`。元素表达式可以是以下任意一种：
- 一个 Int，指定单个元素标签；例如，`1`。
- 一个 String，指定单个元素标签；例如，`'7'`。
- 一个 String，指定元素标签序列；例如，`'3:5'` 和 `'3:15:3'`。

**可选参数**

无。

**返回值**

一个 LeafFromModelElemLabels 对象。

**异常**

无。

### 16.17.2 成员

LeafFromModelElemLabels 对象的成员与 [LeafFromModelElemLabels](pt01ch16pyo17.md#ker-leaffrommodelelemlabels-leaffrommodelelemlabels-pyc) 方法的参数具有相同的名称和描述。

此外，LeafFromModelElemLabels 对象还有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





