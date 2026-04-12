# 29.52 FailureRatios 对象

FailureRatios 对象为 [Concrete](pt01ch29pyo18.md) 模型指定失效面的形状。

**访问**

```
import material
mdb.models[*name*].materials[*name*].concrete.failureRatios
import odbMaterial
session.odbs[*name*].materials[*name*].concrete.failureRatios
```

### 29.52.1 FailureRatios(...)

此方法创建 FailureRatios 对象。

**路径**

```
mdb.models[*name*].materials[*name*].concrete.FailureRatios
session.odbs[*name*].materials[*name*].concrete.FailureRatios
```

**必需参数**

*table*

 Float 元组序列，指定下述项目。

**可选参数**

*temperatureDependency*

 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

- 极限双轴压应力与单轴压缩极限应力之比。默认值为 1.16。
- 失效时单轴拉应力与单轴压应力失效值之比的绝对值。默认值为 0.09。
- 双轴压缩时主塑性应变分量与单轴压缩时极限应力下塑性应变之比。默认值为 1.28。
- 当另一个非零主应变分量处于极限压应力值时，平面应力中剪切时的主拉应力值与单轴拉伸下开裂应力之比。默认值为 1/3。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

 FailureRatios 对象。

**异常**

 RangeError。

### 29.52.2 setValues(...)

此方法修改 FailureRatios 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [FailureRatios](pt01ch29pyo52.md#ker-failureratios-failureratios-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.52.3 成员

FailureRatios 对象的成员与 [FailureRatios](pt01ch29pyo52.md#ker-failureratios-failureratios-pyc) 方法的参数具有相同的名称和描述。

### 29.52.4 对应的分析关键字

| [*FAILURE RATIOS](../key/key-link.md#usb-kws-mfailureratios) |
| --- |
