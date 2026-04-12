# 21.5 ExpressionField 对象





ExpressionField 对象定义一个空间变化场，其值根据用户提供的数学表达式计算。

ExpressionField 对象派生自 [AnalyticalField](pt01ch21pyo02.md) 对象。

**访问**

```
import fields
mdb.models[*name*].analyticalFields[*name*]
```

### 21.5.1 ExpressionField(...)

此方法创建 ExpressionField 对象。

**路径**

```
mdb.models[*name*].ExpressionField
```

**必需参数**

*name*

一个 String，指定存储库键。

*expression*

一个 String，指定要在空间中求值的 Python 表达式。变量为 X、Y 和 Z；或 R、Th 和 Z；或基于所选坐标系的 R、Th 和 P。

**可选参数**

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定场的局部坐标系。如果 *localCsys*=`None`，则场在全局坐标系中定义。默认值为 `None`。

*description*

一个 String，指定场的描述。默认值为空字符串。

**返回值**

一个 ExpressionField 对象。

**异常**

TextException。

### 21.5.2 setValues(...)

此方法修改 ExpressionField 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ExpressionField](pt01ch21pyo05.md#ker-expressionfield-expressionfield-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 21.5.3 成员

ExpressionField 对象具有与 [ExpressionField](pt01ch21pyo05.md#ker-expressionfield-expressionfield-pyc) 方法的参数相同的名称和描述的成员。





