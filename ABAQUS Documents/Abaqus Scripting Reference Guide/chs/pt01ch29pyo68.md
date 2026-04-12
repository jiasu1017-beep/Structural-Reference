# 29.68 MagneticPermeability 对象

MagneticPermeability 对象指定磁导率。

**访问**

```
import material
mdb.models[*name*].materials[*name*].magneticPermeability
import odbMaterial
session.odbs[*name*].materials[*name*].magneticPermeability
```

### 29.68.1 MagneticPermeability(...)

此方法创建 MagneticPermeability 对象。

**路径**

```
mdb.models[*name*].materials[*name*].MagneticPermeability
session.odbs[*name*].materials[*name*].MagneticPermeability
```

**必需参数**

*table*

Float 元组序列，指定下述项目。

*table2*

Float 元组序列，如果 Nonlinear BH 选项为真，则必须指定 table2。table2 的项目与 table 类似，但针对第二方向。

*table3*

Float 元组序列，如果 Nonlinear BH 选项为真，则必须指定 table3。table3 的项目与 table 类似，但针对第三方向。

**可选参数**

*type*

SymbolicConstant，指定磁导率类型。可能的值为 ISOTROPIC、ORTHOTROPIC 和 ANISOTROPIC。默认值为 ISOTROPIC。

*frequencyDependency*

Boolean，指定数据是否依赖于频率。默认值为 OFF。

*temperatureDependency*

Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

Int，指定场变量依赖项的数量。默认值为 0。

*nonlinearBH*

Boolean，指定磁行为是否非线性，以及是否以磁通密度与磁场值的表格形式可用。默认值为 OFF。

**表格数据**

如果 *type*=ISOTROPIC，表格数据指定以下内容：
- 磁导率。
- 频率（如果数据依赖于频率）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=ISOTROPIC 且 *nonlinearBH*=TRUE，表格数据指定以下内容：
- 磁通密度向量的大小。
- 磁场向量的大小。
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

如果 *type*=ANISOTROPIC 且 *nonlinearBH*=TRUE，表格数据指定以下内容：
- 第一方向磁通密度向量的大小。
- 第二方向磁场向量的大小。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

MagneticPermeability 对象。

**异常**

RangeError。

### 29.68.2 setValues(...)

此方法修改 MagneticPermeability 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [MagneticPermeability](pt01ch29pyo68.md#ker-magneticpermeability-magneticpermeability-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.68.3 成员

MagneticPermeability 对象的成员与 [MagneticPermeability](pt01ch29pyo68.md#ker-magneticpermeability-magneticpermeability-pyc) 方法的参数具有相同的名称和描述。

### 29.68.4 对应的分析关键字

| [*MAGNETIC PERMEABILITY](../key/key-link.md#usb-kws-mmagpermeability) |
| --- |
