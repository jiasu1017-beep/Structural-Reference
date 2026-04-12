# 29.46 ElectricalConductivity 对象

ElectricalConductivity 对象指定电导率。

**访问**

```
import material
mdb.models[*name*].materials[*name*].electricalConductivity
import odbMaterial
session.odbs[*name*].materials[*name*].electricalConductivity
```

### 29.46.1 ElectricalConductivity(...)

此方法创建 ElectricalConductivity 对象。

**路径**

```
mdb.models[*name*].materials[*name*].ElectricalConductivity
session.odbs[*name*].materials[*name*].ElectricalConductivity
```

**必需参数**

*table*

 Float 元组序列，指定下述项目。

**可选参数**

*type*

 SymbolicConstant，指定电导率类型。可能的值为 ISOTROPIC、ORTHOTROPIC 和 ANISOTROPIC。默认值为 ISOTROPIC。

*frequencyDependency*

 Boolean，指定数据是否依赖于频率。默认值为 OFF。

*temperatureDependency*

 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

**表格数据**

如果 *type*=ISOTROPIC，表格数据指定以下内容：
- 电导率。
- 频率（如果数据依赖于频率）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=ORTHOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00221.gif)。
- ![](../graphics/ker_eqn00222.gif)。
- ![](../graphics/ker_eqn00223.gif)。
- 频率（如果数据依赖于频率）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=ANISOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00221.gif)。
- ![](../graphics/ker_eqn00224.gif)。
- ![](../graphics/ker_eqn00222.gif)。
- ![](../graphics/ker_eqn00225.gif)。
- ![](../graphics/ker_eqn00226.gif)。
- ![](../graphics/ker_eqn00223.gif)。
- 频率（如果数据依赖于频率）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

 ElectricalConductivity 对象。

**异常**

 RangeError。

### 29.46.2 setValues(...)

此方法修改 ElectricalConductivity 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [ElectricalConductivity](pt01ch29pyo46.md#ker-electricalconductivity-electricalconductivity-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.46.3 成员

ElectricalConductivity 对象的成员与 [ElectricalConductivity](pt01ch29pyo46.md#ker-electricalconductivity-electricalconductivity-pyc) 方法的参数具有相同的名称和描述。

### 29.46.4 对应的分析关键字

| [*ELECTRICAL CONDUCTIVITY](../key/key-link.md#usb-kws-melectricconduct) |
| --- |
