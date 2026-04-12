# 29.53 FluidLeakoff 对象

FluidLeakoff 对象为孔隙压力相干元素指定渗漏系数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].fluidLeakoff
import odbMaterial
session.odbs[*name*].materials[*name*].fluidLeakoff
```

### 29.53.1 FluidLeakoff(...)

此方法创建 FluidLeakoff 对象。

**路径**

```
mdb.models[*name*].materials[*name*].FluidLeakoff
session.odbs[*name*].materials[*name*].FluidLeakoff
```

**必需参数**

无。

**可选参数**

*temperatureDependency*

 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

*type*

 SymbolicConstant，指定流体渗漏类型。可能的值为 COEFFICIENTS 和 USER。默认值为 COEFFICIENTS。

*table*

 Float 元组序列，指定下述项目。默认值为空序列。

**表格数据**

表格数据指定以下内容：
- 顶部单元表面的流体渗漏系数。
- 底部单元表面的流体渗漏系数。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 以此类推。

**返回值**

 FluidLeakoff 对象。

**异常**

无。

### 29.53.2 setValues(...)

此方法修改 FluidLeakoff 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [FluidLeakoff](pt01ch29pyo53.md#ker-fluidleakoff-fluidleakoff-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.53.3 成员

FluidLeakoff 对象的成员与 [FluidLeakoff](pt01ch29pyo53.md#ker-fluidleakoff-fluidleakoff-pyc) 方法的参数具有相同的名称和描述。

### 29.53.4 对应的分析关键字

| [*FLUID LEAKOFF](../key/key-link.md#usb-kws-mfluidleakoff) |
| --- |
