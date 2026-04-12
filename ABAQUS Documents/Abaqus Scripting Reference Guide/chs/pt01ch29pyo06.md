# 29.6 BrittleFailure 对象





BrittleFailure 对象指定材料的脆性失效。

**访问**

```
import material
mdb.models[*name*].materials[*name*].brittleCracking.brittleFailure
import odbMaterial
session.odbs[*name*].materials[*name*].brittleCracking.brittleFailure
```

### 29.6.1 BrittleFailure(...)

此方法创建 BrittleFailure 对象。

**路径**

```
mdb.models[*name*].materials[*name*].brittleCracking.BrittleFailure
session.odbs[*name*].materials[*name*].brittleCracking.BrittleFailure
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

*failureCriteria*

一个 SymbolicConstant，指定失效标准。可能的值为 UNIDIRECTIONAL、BIDIRECTIONAL 和 TRIDIRECTIONAL。默认值为 UNIDIRECTIONAL。

**表格数据**

如果父级 [BrittleCracking](pt01ch29pyo05.md) 成员 *type*=STRAIN，表格数据指定以下内容：
- 直接裂隙失效应变。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果父级 [BrittleCracking](pt01ch29pyo05.md) 成员 *type*=DISPLACEMENT 或 *type*=GFI，表格数据指定以下内容：
- 直接裂隙失效位移。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 BrittleFailure 对象。

**异常**

RangeError。

### 29.6.2 setValues(...)

此方法修改 BrittleFailure 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BrittleFailure](pt01ch29pyo06.md#ker-brittlefailure-brittlefailure-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.6.3 成员

BrittleFailure 对象具有与 [BrittleFailure](pt01ch29pyo06.md#ker-brittlefailure-brittlefailure-pyc) 方法参数同名的成员，描述也相同。

### 29.6.4 对应的分析关键字

| [*BRITTLE FAILURE](../key/key-link.md#usb-kws-mbrittlefailure) |
| --- |




