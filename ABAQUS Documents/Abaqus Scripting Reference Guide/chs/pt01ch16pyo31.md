# 16.30 LeafFromPartInstance 对象









LeafFromPartInstance 对象可在需要 [Leaf](pt01ch16pyo04.md) 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromPartInstance 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupOdbToolset
```

### 16.30.1 LeafFromPartInstance(...)

此方法从部件实例名称列表创建 [Leaf](pt01ch16pyo04.md) 对象。

**路径**

```
LeafFromPartInstance
```

**必需参数**

*partInstanceName*

一个 String 序列，指定部件实例的名称。

**可选参数**

无。

**返回值**

一个 LeafFromPartInstance 对象。

**异常**

无。

### 16.30.2 成员

LeafFromPartInstance 对象的成员与 [LeafFromPartInstance](pt01ch16pyo30.md#ker-leaffrompartinstance-leaffrompartinstance-pyc) 方法的参数具有相同的名称和描述。

此外，LeafFromPartInstance 对象还有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





