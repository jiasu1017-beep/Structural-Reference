# 29.45 Elastic 对象

Elastic 对象指定弹性材料属性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].elastic
import odbMaterial
session.odbs[*name*].materials[*name*].elastic
```

### 29.45.1 Elastic(...)

此方法创建 Elastic 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Elastic
session.odbs[*name*].materials[*name*].Elastic
```

**必需参数**

*table*

 Float 元组序列，指定下述项目。

**可选参数**

*type*

 SymbolicConstant，指定提供的弹性数据类型。可能的值为：
- ISOTROPIC
- ORTHOTROPIC
- ANISOTROPIC
- ENGINEERING_CONSTANTS
- LAMINA
- TRACTION
- COUPLED_TRACTION
- SHORT_FIBER
- SHEAR

默认值为 ISOTROPIC。

*noCompression*

 Boolean，指定是否允许压应力。默认值为 OFF。

*noTension*

 Boolean，指定是否允许拉应力。默认值为 OFF。

*temperatureDependency*

 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

*moduli*

 SymbolicConstant，指定弹性材料常数的时间依赖性。可能的值为 INSTANTANEOUS 和 LONG_TERM。默认值为 LONG_TERM。

**表格数据**

如果 *type*=ISOTROPIC，表格数据指定以下内容：
- 杨氏模量，![](../graphics/ker_eqn00163.gif)。
- 泊松比，![](../graphics/ker_eqn00164.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=SHEAR，表格数据指定以下内容：
- 剪切模量，![](../graphics/ker_eqn00182.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=ENGINEERING_CONSTANTS，表格数据指定以下内容：
- ![](../graphics/ker_eqn00183.gif)。
- ![](../graphics/ker_eqn00184.gif)。
- ![](../graphics/ker_eqn00185.gif)。
- ![](../graphics/ker_eqn00186.gif)。
- ![](../graphics/ker_eqn00187.gif)。
- ![](../graphics/ker_eqn00188.gif)。
- ![](../graphics/ker_eqn00189.gif)。
- ![](../graphics/ker_eqn00190.gif)。
- ![](../graphics/ker_eqn00191.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=LAMINA，表格数据指定以下内容：
- ![](../graphics/ker_eqn00183.gif)。
- ![](../graphics/ker_eqn00184.gif)。
- ![](../graphics/ker_eqn00186.gif)。
- ![](../graphics/ker_eqn00189.gif)。
- ![](../graphics/ker_eqn00190.gif)。此剪切模量用于定义壳中的横向剪切行为。
- ![](../graphics/ker_eqn00191.gif)。此剪切模量用于定义壳中的横向剪切行为。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=ORTHOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00192.gif)。
- ![](../graphics/ker_eqn00193.gif)。
- ![](../graphics/ker_eqn00194.gif)。
- ![](../graphics/ker_eqn00195.gif)。
- ![](../graphics/ker_eqn00196.gif)。
- ![](../graphics/ker_eqn00197.gif)。
- ![](../graphics/ker_eqn00198.gif)。
- ![](../graphics/ker_eqn00199.gif)。
- ![](../graphics/ker_eqn00200.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=ANISOTROPIC，表格数据指定以下内容：
- ![](../graphics/ker_eqn00192.gif)。
- ![](../graphics/ker_eqn00193.gif)。
- ![](../graphics/ker_eqn00194.gif)。
- ![](../graphics/ker_eqn00195.gif)。
- ![](../graphics/ker_eqn00196.gif)。
- ![](../graphics/ker_eqn00197.gif)。
- ![](../graphics/ker_eqn00201.gif)。
- ![](../graphics/ker_eqn00202.gif)。
- ![](../graphics/ker_eqn00203.gif)。
- ![](../graphics/ker_eqn00198.gif)。
- ![](../graphics/ker_eqn00204.gif)。
- ![](../graphics/ker_eqn00205.gif)。
- ![](../graphics/ker_eqn00206.gif)。
- ![](../graphics/ker_eqn00207.gif)。
- ![](../graphics/ker_eqn00199.gif)。
- ![](../graphics/ker_eqn00208.gif)。
- ![](../graphics/ker_eqn00209.gif)。
- ![](../graphics/ker_eqn00210.gif)。
- ![](../graphics/ker_eqn00211.gif)。
- ![](../graphics/ker_eqn00212.gif)。
- ![](../graphics/ker_eqn00200.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=TRACTION，表格数据指定以下内容：
- 对于翘曲元素为 ![](../graphics/ker_eqn00163.gif)；对于相干元素为 ![](../graphics/ker_eqn00213.gif)。
- 对于翘曲元素为 ![](../graphics/ker_eqn00214.gif)；对于相干元素为 ![](../graphics/ker_eqn00215.gif)。
- 对于翘曲元素为 ![](../graphics/ker_eqn00216.gif)；对于相干元素为 ![](../graphics/ker_eqn00217.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=COUPLED_TRACTION，表格数据指定以下内容：
- ![](../graphics/ker_eqn00213.gif)。
- ![](../graphics/ker_eqn00215.gif)。
- ![](../graphics/ker_eqn00217.gif)。
- ![](../graphics/ker_eqn00218.gif)。
- ![](../graphics/ker_eqn00219.gif)。
- ![](../graphics/ker_eqn00220.gif)。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

如果 *type*=SHORT_FIBER，则没有表格数据。

**返回值**

 Elastic 对象。

**异常**

 RangeError。

### 29.45.2 setValues(...)

此方法修改 Elastic 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [Elastic](pt01ch29pyo45.md#ker-elastic-elastic-pyc) 方法的参数相同。

**返回值**

无

**异常**

 RangeError。

### 29.45.3 成员

Elastic 对象的成员与 [Elastic](pt01ch29pyo45.md#ker-elastic-elastic-pyc) 方法的参数具有相同的名称和描述。

此外，Elastic 对象可以具有以下成员：

*failStress*

 [FailStress](pt01ch29pyo51.md) 对象。

*failStrain*

 [FailStrain](pt01ch29pyo50.md) 对象。

### 29.45.4 对应的分析关键字

| [*ELASTIC](../key/key-link.md#usb-kws-melastic) |
| --- |
