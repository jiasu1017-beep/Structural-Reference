# 16.7 LeafFromElementLabels 对象









LeafFromElementLabels 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromElementLabels 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupOdbToolset
```

### 16.7.1 LeafFromElementLabels(...)

此方法从属于单个部件实例的元素标签序列创建 [Leaf](pt01ch16pyo04.md) 对象。

**路径**

```
LeafFromElementLabels
```

**必需参数**

*partInstanceName*

一个 String，指定 *elementLabels* 所引用的部件实例的名称。

*elementLabels*

一个 String 序列，指定表示元素标签的表达式。表达式可以是以下任意一种：
- 一个 Int，指定单个元素标签；例如，`1`。
- 一个 String，指定单个元素标签；例如，`'7'`。
- 一个 String，指定元素标签序列；例如，`'3:5'` 和 `'3:15:3'`。

**可选参数**

无。

**返回值**

一个 LeafFromElementLabels 对象。

**异常**

无。

### 16.7.2 成员

LeafFromElementLabels 对象的成员与 [LeafFromElementLabels](pt01ch16pyo07.md#ker-leaffromelementlabels-leaffromelementlabels-pyc) 方法的参数具有相同的名称和描述。

此外，LeafFromElementLabels 对象还有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





