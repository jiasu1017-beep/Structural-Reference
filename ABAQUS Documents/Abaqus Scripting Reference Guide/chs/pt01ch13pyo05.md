# 13.5 EmbeddedRegion 对象

EmbeddedRegion 对象允许您将模型的某个区域嵌入到模型的"宿主"区域中或整个模型中。

EmbeddedRegion 对象派生自 [Constraint](pt01ch13pyo01.md) 对象。

**访问权限**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.5.1 EmbeddedRegion(...)

此方法创建一个 EmbeddedRegion 对象。

**路径**

```
mdb.models[*name*].EmbeddedRegion
```

**必需参数**

*name*

字符串，指定约束存储库键。

*embeddedRegion*

[Region](pt01ch45pyo03.md) 对象，指定要嵌入的主体区域。

*hostRegion*

[Region](pt01ch45pyo03.md) 对象，指定宿主区域。值为 `None` 表示宿主区域是整个模型。

**可选参数**

*weightFactorTolerance*

浮点数，指定权重因子被清零的下限值。默认值为 10⁻⁶。

*toleranceMethod*

符号常量，指定用于确定嵌入单元容差的方法。可能的值为 ABSOLUTE、FRACTIONAL 和 BOTH。默认值为 BOTH。

*absoluteTolerance*

浮点数，指定嵌入区域上的节点可能位于宿主区域外部的绝对值。如果 *absoluteTolerance*=0.0，则使用 *fractionalTolerance* 值。默认值为 0.0。

此参数仅在 *toleranceMethod*=ABSOLUTE 或 BOTH 时适用。

*fractionalTolerance*

浮点数，指定嵌入区域上的节点可能位于宿主区域外部的分数值。该分数值基于宿主区域内的平均单元大小。默认值为 0.05。

如果同时指定了两个容差参数，则使用较小的值。

此参数仅在 *toleranceMethod*=FRACTIONAL 或 BOTH 时适用。

**返回值**

EmbeddedRegion 对象。

**异常**

无。

### 13.5.2 setValues(...)

此方法修改 EmbeddedRegion 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [EmbeddedRegion](pt01ch13pyo05.md#ker-embeddedregion-embeddedregion-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 13.5.3 成员

EmbeddedRegion 对象的成员与 [EmbeddedRegion](pt01ch13pyo05.md#ker-embeddedregion-embeddedregion-pyc) 方法的参数具有相同的名称和描述。

此外，EmbeddedRegion 对象还有以下成员：

*suppressed*

布尔值，指定约束是否被抑制。默认值为 OFF。

### 13.5.4 对应的分析关键字

| [*EMBEDDED ELEMENT](../key/key-link.md#usb-kws-membeddedelement) |
| --- |

