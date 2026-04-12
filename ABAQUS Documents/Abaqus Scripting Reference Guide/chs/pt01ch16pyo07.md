# 16.8 LeafFromElementSets 对象









LeafFromElementSets 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromElementSets 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupOdbToolset
```

### 16.8.1 LeafFromElementSets(...)

此方法从元素集序列创建 [Leaf](pt01ch16pyo04.md) 对象。

**路径**

```
LeafFromElementSets
```

**必需参数**

*elementSets*

一个 String 序列，指定元素集；或一个 String，指定单个元素集。

**可选参数**

无。

**返回值**

一个 LeafFromElementSets 对象。

**异常**

无。

### 16.8.2 成员

LeafFromElementSets 对象的成员与 [LeafFromElementSets](pt01ch16pyo08.md#ker-leaffromelementsets-leaffromelementsets-pyc) 方法的参数具有相同的名称和描述。

此外，LeafFromElementSets 对象还有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





