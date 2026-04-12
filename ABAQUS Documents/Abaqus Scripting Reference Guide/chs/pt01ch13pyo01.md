# 13.2 AdjustPoints 对象

AdjustPoints 约束对象用于将点（节点）调整到曲面。

AdjustPoints 对象派生自 [Constraint](pt01ch13pyo01.md) 对象。

**访问权限**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.2.1 AdjustPoints(...)

此方法创建一个 AdjustPoints 对象。

**路径**

```
mdb.models[*name*].AdjustPoints
```

**必需参数**

*name*

字符串，指定约束存储库键。

*surface*

[Region](pt01ch45pyo03.md) 对象，指定 *controlPoints* 要调整到的曲面。

*controlPoints*

[Region](pt01ch45pyo03.md) 对象，指定约束控制点。

**可选参数**

无。

**返回值**

AdjustPoints 对象。

**异常**

无。

### 13.2.2 setValues(...)

此方法修改 AdjustPoints 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [AdjustPoints](pt01ch13pyo02.md#ker-adjustpoints-adjustpoints-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 13.2.3 成员

AdjustPoints 对象的成员与 [AdjustPoints](pt01ch13pyo02.md#ker-adjustpoints-adjustpoints-pyc) 方法的参数具有相同的名称和描述。

此外，AdjustPoints 对象还有以下成员：

*suppressed*

布尔值，指定约束是否被抑制。默认值为 OFF。

### 13.2.4 对应的分析关键字

| [*ADJUST](../key/key-link.md#usb-kws-madjust) |
| --- |

