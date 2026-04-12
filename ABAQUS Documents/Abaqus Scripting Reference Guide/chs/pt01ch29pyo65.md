# 29.65 JouleHeatFraction 对象

JouleHeatFraction 对象定义作为热量释放的电能的分数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].jouleHeatFraction
import odbMaterial
session.odbs[*name*].materials[*name*].jouleHeatFraction
```

### 29.65.1 JouleHeatFraction(...)

此方法创建 JouleHeatFraction 对象。

**路径**

```
mdb.models[*name*].materials[*name*].JouleHeatFraction
session.odbs[*name*].materials[*name*].JouleHeatFraction
```

**必需参数**

无。

**可选参数**

*fraction*

Float，指定作为热量释放的电能的分数，包括任何单位转换因子。可能的值为 0.0 ≤ *fraction* ≤ 1.0。默认值为 1.0。

**返回值**

JouleHeatFraction 对象。

**异常**

RangeError。

### 29.65.2 setValues(...)

此方法修改 JouleHeatFraction 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [JouleHeatFraction](pt01ch29pyo65.md#ker-jouleheatfraction-jouleheatfraction-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.65.3 成员

JouleHeatFraction 对象的成员与 [JouleHeatFraction](pt01ch29pyo65.md#ker-jouleheatfraction-jouleheatfraction-pyc) 方法的参数具有相同的名称和描述。

### 29.65.4 对应的分析关键字

| [*JOULE HEAT FRACTION](../key/key-link.md#usb-kws-mjouleheatfrac) |
| --- |
