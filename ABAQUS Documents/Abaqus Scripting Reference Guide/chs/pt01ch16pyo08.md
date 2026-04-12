# 16.6 LeafFromDisplayGroup 对象









LeafFromDisplayGroup 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromDisplayGroup 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupMdbToolset
import displayGroupOdbToolset
```

### 16.6.1 LeafFromDisplayGroup(...)

此方法从 Display Group 对象序列创建 [Leaf](pt01ch16pyo04.md) 对象。

**路径**

```
LeafFromDisplayGroup
```

**必需参数**

*displayGroup*

一个 [DisplayGroupArray](pt01ch16pyo01.md) 对象。

**可选参数**

无。

**返回值**

一个 LeafFromDisplayGroup 对象。

**异常**

无。

### 16.6.2 成员

LeafFromDisplayGroup 对象的成员与 [LeafFromDisplayGroup](pt01ch16pyo06.md#ker-leaffromdisplaygroup-leaffromdisplaygroup-pyc) 方法的参数具有相同的名称和描述。

此外，LeafFromDisplayGroup 对象还有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





