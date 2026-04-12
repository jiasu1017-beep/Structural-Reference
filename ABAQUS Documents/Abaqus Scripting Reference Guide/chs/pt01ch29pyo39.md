# 29.39 DetonationPoint 对象





DetonationPoint 对象是 Eos 对象的子选项。DetonationPoint 对象为流体动力学材料定义各向同性线性弹性剪切或线性粘性剪切行为。

**访问**

```
import material
mdb.models[*name*].materials[*name*].eos.detonationPoint
import odbMaterial
session.odbs[*name*].materials[*name*].eos.detonationPoint
```

### 29.39.1 DetonationPoint(...)

此方法创建 DetonationPoint 对象。

**路径**

```
mdb.models[*name*].materials[*name*].eos.DetonationPoint
session.odbs[*name*].materials[*name*].eos.DetonationPoint
```

**必需参数**

*table*

一个 Float 元组序列，指定如下所述的项目。

**可选参数**

无。

**表格数据**

- 起爆点坐标的 X 值。
- 起爆点坐标的 Y 值。
- 起爆点坐标的 Z 值。
- 起爆延迟时间。

**返回值**

一个 DetonationPoint 对象。

**异常**

无。

### 29.39.2 setValues(...)

此方法修改 DetonationPoint 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DetonationPoint](pt01ch29pyo39.md#ker-detonationpoint-detonationpoint-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.39.3 成员

DetonationPoint 对象具有与 [DetonationPoint](pt01ch29pyo39.md#ker-detonationpoint-detonationpoint-pyc) 方法参数同名的成员，描述也相同。

### 29.39.4 对应的分析关键字

| [*DETONATION POINT](../key/key-link.md#usb-kws-mdetonationpt) |
| --- |




