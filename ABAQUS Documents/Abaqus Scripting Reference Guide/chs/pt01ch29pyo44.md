# 29.44 DruckerPragerHardening 对象

DruckerPragerHardening 对象为 Drucker-Prager 塑性模型指定硬化。

**访问**

```
import material
mdb.models[*name*].materials[*name*].druckerPrager.druckerPragerHardening
import odbMaterial
session.odbs[*name*].materials[*name*].druckerPrager\
.druckerPragerHardening
```

### 29.44.1 DruckerPragerHardening(...)

此方法创建 DruckerPragerHardening 对象。

**路径**

```
mdb.models[*name*].materials[*name*].druckerPrager.DruckerPragerHardening
session.odbs[*name*].materials[*name*].druckerPrager\
.DruckerPragerHardening
```

**必需参数**

*table*

 Float 元组序列，指定下述项目。

**可选参数**

*type*

 SymbolicConstant，指定定义硬化行为的数据类型。可能的值为 COMPRESSION、TENSION 和 SHEAR。默认值为 COMPRESSION。

*rate*

 Boolean，指定数据是否依赖于速率。默认值为 OFF。

*temperatureDependency*

 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

- 屈服应力。
- 对应塑性应变的绝对值。（输入的第一个表格值必须始终为零。）
- 此硬化曲线适用的等效塑性应变率，![](../graphics/ker_eqn00181.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

 DruckerPragerHardening 对象。

**异常**

 RangeError。

### 29.44.2 setValues(...)

此方法修改 DruckerPragerHardening 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [DruckerPragerHardening](pt01ch29pyo44.md#ker-druckerpragerhardening-druckerpragerhardening-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.44.3 成员

DruckerPragerHardening 对象的成员与 [DruckerPragerHardening](pt01ch29pyo44.md#ker-druckerpragerhardening-druckerpragerhardening-pyc) 方法的参数具有相同的名称和描述。

### 29.44.4 对应的分析关键字

| [*DRUCKER PRAGER HARDENING](../key/key-link.md#usb-kws-mdruckerhardening) |
| --- |
