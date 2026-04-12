# 16.4 Leaf 对象

Leaf 对象用于指定显示组中的项。Leaf 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

Leaf 对象与 Set 对象有相似之处；但是，Leaf 对象在评估 DisplayGroup 表达式时进行评估，并且它们可以具有符号常量值（这些值也在评估 DisplayGroup 表达式时进行评估）。

**访问权限**

```
import displayGroupMdbToolset
import displayGroupOdbToolset
```

### 16.4.1 Leaf(...)

此方法创建一个 Leaf 对象。

**路径**

```
Leaf
```

**必需参数**

*leafType*

符号常量，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。

**可选参数**

无。

**返回值**

Leaf 对象。

**异常**

无。

### 16.4.2 成员

Leaf 对象的成员与 [Leaf](pt01ch16pyo04.md#ker-leaf-leaf-pyc) 方法的参数具有相同的名称和描述。

