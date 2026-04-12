# 29.87 Regularization 对象

Regularization 对象定义用于正则化材料数据的容差。

**访问**

```
import material
mdb.models[*name*].materials[*name*].regularization
import odbMaterial
session.odbs[*name*].materials[*name*].regularization
```

### 29.87.1 Regularization(...)

此方法创建 Regularization 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Regularization
session.odbs[*name*].materials[*name*].Regularization
```

**必需参数**

无。

**可选参数**

*rtol*

Float，指定用于正则化材料数据的容差。默认值为 0.03。

*strainRateRegularization*

SymbolicConstant，指定应变率相关材料数据正则化的形式。可能的值为 LOGARITHMIC 和 LINEAR。默认值为 LOGARITHMIC。

**返回值**

Regularization 对象。

**异常**

RangeError。

### 29.87.2 setValues(...)

此方法修改 Regularization 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Regularization](pt01ch29pyo87.md#ker-regularization-regularization-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.87.3 成员

Regularization 对象的成员与 [Regularization](pt01ch29pyo87.md#ker-regularization-regularization-pyc) 方法的参数具有相同的名称和描述。

### 29.87.4 对应的分析关键字

| [*DASHPOT](../key/key-link.md#usb-kws-mdashpot) |
| --- |
