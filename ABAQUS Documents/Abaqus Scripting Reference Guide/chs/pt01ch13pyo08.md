# 13.6 Equation 对象

Equation 对象定义了一组自由度之间的线性多点约束。

Equation 对象派生自 [Constraint](pt01ch13pyo01.md) 对象。

**访问权限**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.6.1 Equation(...)

此方法创建一个 Equation 对象。

**路径**

```
mdb.models[*name*].Equation
```

**必需参数**

*name*

字符串，指定约束存储库键。

*terms*

（浮点数、字符串、整数、整数）序列的序列，指定系数、Set 名称、自由度和坐标系 ID。坐标系 ID 是可选的。

**可选参数**

无。

**返回值**

Equation 对象。

**异常**

如果 *terms* 不包含多个条目：

```
Equation must have two or more terms.
```

### 13.6.2 setValues(...)

此方法修改 Equation 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Equation](pt01ch13pyo06.md#ker-equation-equation-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

如果 *terms* 不包含多个条目：

```
Equation must have two or more terms.
```

### 13.6.3 成员

Equation 对象的成员与 [Equation](pt01ch13pyo06.md#ker-equation-equation-pyc) 方法的参数具有相同的名称和描述。

此外，Equation 对象还有以下成员：

*suppressed*

布尔值，指定约束是否被抑制。默认值为 OFF。

### 13.6.4 对应的分析关键字

| [*EQUATION](../key/key-link.md#usb-kws-mequation) |
| --- |

