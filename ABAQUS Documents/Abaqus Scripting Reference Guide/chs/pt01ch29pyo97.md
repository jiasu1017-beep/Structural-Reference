# 29.97 TensionCutOff 对象

TensionCutOff 对象为不同材料模型（例如摩尔-库仑塑性模型）指定张力截止。

**访问**

```
import material
mdb.models[*name*].materials[*name*].mohrCoulombPlasticity.tensionCutOff
import odbMaterial
session.odbs[*name*].materials[*name*].mohrCoulombPlasticity.tensionCutOff
```

### 29.97.1 TensionCutOff(...)

此方法创建 TensionCutOff 对象。

**路径**

```
mdb.models[*name*].materials[*name*].mohrCoulombPlasticity.TensionCutOff
session.odbs[*name*].materials[*name*].mohrCoulombPlasticity.TensionCutOff
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

- 张力截止应力。
- 对应拉伸塑性应变的值。（输入的第一个表格值必须始终为零。）
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

TensionCutOff 对象。

**异常**

RangeError。

### 29.97.2 setValues(...)

此方法修改 TensionCutOff 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [TensionCutOff](pt01ch29pyo97.md#ker-tensioncutoff-tensioncutoff-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.97.3 成员

TensionCutOff 对象的成员与 [TensionCutOff](pt01ch29pyo97.md#ker-tensioncutoff-tensioncutoff-pyc) 方法的参数具有相同的名称和描述。

### 29.97.4 对应的分析关键字

| [*TENSION CUTOFF](../key/key-link.md#usb-kws-mtensioncutoff) |
| --- |
