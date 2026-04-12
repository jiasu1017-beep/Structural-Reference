# 29.29 CycledPlastic 对象





CycledPlastic 对象为 ORNL 本构模型指定循环屈服应力数据。

**访问**

```
import material
mdb.models[*name*].materials[*name*].plastic.cycledPlastic
import odbMaterial
session.odbs[*name*].materials[*name*].plastic.cycledPlastic
```

### 29.29.1 CycledPlastic(...)

此方法创建 CycledPlastic 对象。

**路径**

```
mdb.models[*name*].materials[*name*].plastic.CycledPlastic
session.odbs[*name*].materials[*name*].plastic.CycledPlastic
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

**表格数据**

- 屈服应力。
- 塑性应变。
- 温度（如果数据依赖于温度）。

**返回值**

一个 CycledPlastic 对象。

**异常**

无。

### 29.29.2 setValues(...)

此方法修改 CycledPlastic 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CycledPlastic](pt01ch29pyo29.md#ker-cycledplastic-cycledplastic-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.29.3 成员

CycledPlastic 对象具有与 [CycledPlastic](pt01ch29pyo29.md#ker-cycledplastic-cycledplastic-pyc) 方法参数同名的成员，描述也相同。

### 29.29.4 对应的分析关键字

| [*CYCLED PLASTIC](../key/key-link.md#usb-kws-mcycledplastic) |
| --- |




