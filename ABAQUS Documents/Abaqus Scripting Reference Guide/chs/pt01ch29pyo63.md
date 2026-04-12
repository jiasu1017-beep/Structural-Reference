# 29.63 Hysteresis 对象

Hysteresis 对象指定弹性体滞后行为材料模型的蠕变部分。

**访问**

```
import material
mdb.models[*name*].materials[*name*].hyperelastic.hysteresis
import odbMaterial
session.odbs[*name*].materials[*name*].hyperelastic.hysteresis
```

### 29.63.1 Hysteresis(...)

此方法创建 Hysteresis 对象。

**路径**

```
mdb.models[*name*].materials[*name*].hyperelastic.Hysteresis
session.odbs[*name*].materials[*name*].hyperelastic.Hysteresis
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

**可选参数**

无。

**表格数据**

- 应力缩放因子。
- 蠕变参数。
- 有效应力指数。
- 蠕变应变指数。

**返回值**

Hysteresis 对象。

**异常**

RangeError。

### 29.63.2 setValues(...)

此方法修改 Hysteresis 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Hysteresis](pt01ch29pyo63.md#ker-hysteresis-hysteresis-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.63.3 成员

Hysteresis 对象的成员与 [Hysteresis](pt01ch29pyo63.md#ker-hysteresis-hysteresis-pyc) 方法的参数具有相同的名称和描述。

### 29.63.4 对应的分析关键字

| [*HYSTERESIS](../key/key-link.md#usb-kws-mhysteresis) |
| --- |
