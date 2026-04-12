# 16.11 LeafFromInstance 对象









LeafFromInstance 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromInstance 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupMdbToolset
```

### 16.11.1 LeafFromInstance(...)

此方法从部件实例对象序列创建 Leaf 对象。

**路径**

```
LeafFromInstance
```

**必需参数**

*instances*

一个 [PartInstance](pt01ch06pyo04.md) 对象或 [PartInstance](pt01ch06pyo04.md) 对象序列。

**可选参数**

无。

**返回值**

一个 LeafFromInstance 对象。

**异常**

如果向此方法传递了无效参数：

```
Cannot define empty leaf.
```

### 16.11.2 成员

LeafFromInstance 对象有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





