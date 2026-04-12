# 29.30 CyclicHardening 对象





CyclicHardening 对象定义非线性各向同性/运动硬化模型的弹性域演化。

**访问**

```
import material
mdb.models[*name*].materials[*name*].plastic.cyclicHardening
import odbMaterial
session.odbs[*name*].materials[*name*].plastic.cyclicHardening
```

### 29.30.1 CyclicHardening(...)

此方法创建 CyclicHardening 对象。

**路径**

```
mdb.models[*name*].materials[*name*].plastic.CyclicHardening
session.odbs[*name*].materials[*name*].plastic.CyclicHardening
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

*parameters*

一个 Boolean，指定材料参数是否直接输入。默认值为 OFF。

**表格数据**

- 等效应力。
- ![](../graphics/ker_eqn00160.gif)（仅当 *parameters*=ON 时）。
- 硬化参数（仅当 *parameters*=ON 时）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 CyclicHardening 对象。

**异常**

无。

### 29.30.2 setValues(...)

此方法修改 CyclicHardening 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CyclicHardening](pt01ch29pyo30.md#ker-cyclichardening-cyclichardening-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.30.3 成员

CyclicHardening 对象具有与 [CyclicHardening](pt01ch29pyo30.md#ker-cyclichardening-cyclichardening-pyc) 方法参数同名的成员，描述也相同。

### 29.30.4 对应的分析关键字

| [*CYCLIC HARDENING](../key/key-link.md#usb-kws-mcyclichardening) |
| --- |




