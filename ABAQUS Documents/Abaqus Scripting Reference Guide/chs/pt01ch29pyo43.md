# 29.43 DruckerPragerCreep 对象

DruckerPragerCreep 对象为 Drucker-Prager 塑性模型指定蠕变。

**访问**

```
import material
mdb.models[*name*].materials[*name*].druckerPrager.druckerPragerCreep
import odbMaterial
session.odbs[*name*].materials[*name*].druckerPrager.druckerPragerCreep
```

### 29.43.1 DruckerPragerCreep(...)

此方法创建 DruckerPragerCreep 对象。

**路径**

```
mdb.models[*name*].materials[*name*].druckerPrager.DruckerPragerCreep
session.odbs[*name*].materials[*name*].druckerPrager.DruckerPragerCreep
```

**必需参数**

*table*

 Float 元组序列，指定下述项目。

**可选参数**

*law*

 SymbolicConstant，指定定义蠕变定律的数据类型。可能的值为：
- STRAIN，指定应变硬化幂律。
- TIME，指定时间硬化幂律。
- SINGHM，指定 Singh-Mitchell 型定律。
- USER，指定蠕变定律从用户子程序 [`CREEP`](../sub/sub-link.md#sub-xsl-creep) 输入。

默认值为 STRAIN。

*temperatureDependency*

 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

如果 *law*=TIME 或 *law*=STRAIN，表格数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。（单位为 [F![](../graphics/ker_eqn00178.gif)L![](../graphics/ker_eqn00179.gif)T![](../graphics/ker_eqn00180.gif)](../popups/usb-int-iconventions-unitsym.md)。）
- ![](../graphics/ker_eqn00088.gif)。
- ![](../graphics/ker_eqn00089.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *law*=SINGHM，表格数据指定以下内容：
- ![](../graphics/ker_eqn00010.gif)。（单位为 [T1](../popups/usb-int-iconventions-unitsym.md)。）
- ![](../graphics/ker_eqn00090.gif)。（单位为 [F1L2](../popups/usb-int-iconventions-unitsym.md)。）
- ![](../graphics/ker_eqn00089.gif)。
- ![](../graphics/ker_eqn00091.gif)。（单位为 [T](../popups/usb-int-iconventions-unitsym.md)。）
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

 DruckerPragerCreep 对象。

**异常**

 RangeError。

### 29.43.2 setValues(...)

此方法修改 DruckerPragerCreep 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [DruckerPragerCreep](pt01ch29pyo43.md#ker-druckerpragercreep-druckerpragercreep-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.43.3 成员

DruckerPragerCreep 对象的成员与 [DruckerPragerCreep](pt01ch29pyo43.md#ker-druckerpragercreep-druckerpragercreep-pyc) 方法的参数具有相同的名称和描述。

### 29.43.4 对应的分析关键字

| [*DRUCKER PRAGER CREEP](../key/key-link.md#usb-kws-mdruckerpragercreep) |
| --- |
