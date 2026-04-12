# 16.9 LeafFromElementVarRange 对象









LeafFromElementVarRange 对象可在需要 Leaf 对象作为参数时使用。[Leaf](pt01ch16pyo04.md) 对象用于指定显示组中的项目。[Leaf](pt01ch16pyo04.md) 对象被构造为临时对象，然后用作 [DisplayGroup](pt01ch16pyo01.md) 命令的参数。

LeafFromElementVarRange 对象派生自 [Leaf](pt01ch16pyo04.md) 对象。

**访问**

```
import displayGroupOdbToolset
```

### 16.9.1 LeafFromElementVarRange(...)

此方法从值位于变量范围内的元素创建 [Leaf](pt01ch16pyo04.md) 对象。

**路径**

```
LeafFromElementVarRange
```

**必需参数**

无。

**可选参数**

*minimumRange*

一个 Float，指定变量范围的最小值。默认值为 3.40282346639E38。

*maximumRange*

一个 Float，指定变量范围的最大值。默认值为 3.40282346639e+038。

*insideRange*

一个 Boolean，指定用于评估范围的方法。如果 *insideRange*=ON，则范围落在指定的最小值和最大值之内。默认值为 ON。

**返回值**

一个 LeafFromElementVarRange 对象。

**异常**

无。

### 16.9.2 成员

LeafFromElementVarRange 对象的成员与 [LeafFromElementVarRange](pt01ch16pyo09.md#ker-leaffromelementvarrange-leaffromelementvarrange-pyc) 方法的参数具有相同的名称和描述。

此外，LeafFromElementVarRange 对象还有以下成员：

*leafType*

一个 SymbolicConstant，指定叶子类型。可能的值为 EMPTY、DEFAULT_MODEL、ALL_ELEMENTS、ALL_NODES 和 ALL_SURFACES。





