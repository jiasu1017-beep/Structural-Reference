# 29.64 InelasticHeatFraction 对象

InelasticHeatFraction 对象定义作为热源出现的非弹性耗散速率的分数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].inelasticHeatFraction
import odbMaterial
session.odbs[*name*].materials[*name*].inelasticHeatFraction
```

### 29.64.1 InelasticHeatFraction(...)

此方法创建 InelasticHeatFraction 对象。

**路径**

```
mdb.models[*name*].materials[*name*].InelasticHeatFraction
session.odbs[*name*].materials[*name*].InelasticHeatFraction
```

**必需参数**

无。

**可选参数**

*fraction*

Float，指定作为单位体积热通量出现的非弹性耗散速率的分数。如有需要，该分数可包含单位转换因子。可能的值为 0.0 ≤ *fraction* ≤ 1.0。默认值为 0.9。

**返回值**

InelasticHeatFraction 对象。

**异常**

RangeError。

### 29.64.2 setValues(...)

此方法修改 InelasticHeatFraction 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [InelasticHeatFraction](pt01ch29pyo64.md#ker-inelasticheatfraction-inelasticheatfraction-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.64.3 成员

InelasticHeatFraction 对象的成员与 [InelasticHeatFraction](pt01ch29pyo64.md#ker-inelasticheatfraction-inelasticheatfraction-pyc) 方法的参数具有相同的名称和描述。

### 29.64.4 对应的分析关键字

| [*INELASTIC HEAT FRACTION](../key/key-link.md#usb-kws-minelastheatfrac) |
| --- |
