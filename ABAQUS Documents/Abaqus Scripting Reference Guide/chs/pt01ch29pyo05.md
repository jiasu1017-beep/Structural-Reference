# 29.5 BrittleCracking 对象





BrittleCracking 对象指定脆裂材料模型的裂隙和裂后特性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].brittleCracking
import odbMaterial
session.odbs[*name*].materials[*name*].brittleCracking
```

### 29.5.1 BrittleCracking(...)

此方法创建 BrittleCracking 对象。

**路径**

```
mdb.models[*name*].materials[*name*].BrittleCracking
session.odbs[*name*].materials[*name*].BrittleCracking
```

**必需参数**

*table*

一个 Float 序列的序列，指定如下所述的项目。

**可选参数**

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖数量。默认值为 0。

*type*

一个 SymbolicConstant，指定裂后行为的类型。可能的值为 STRAIN、DISPLACEMENT 和 GFI。默认值为 STRAIN。

**表格数据**

如果 *type*=STRAIN，表格数据指定以下内容：
- 裂隙后的剩余直接应力。
- 直接裂隙应变。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，表格数据指定以下内容：
- 裂隙后的剩余直接应力。
- 直接裂隙位移。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=GFI，表格数据指定以下内容：
- 失效应力。
- I 型断裂能。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 BrittleCracking 对象。

**异常**

无。

### 29.5.2 setValues(...)

此方法修改 BrittleCracking 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BrittleCracking](pt01ch29pyo05.md#ker-brittlecracking-brittlecracking-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.5.3 成员

BrittleCracking 对象具有与 [BrittleCracking](pt01ch29pyo05.md#ker-brittlecracking-brittlecracking-pyc) 方法参数同名的成员，描述也相同。

此外，BrittleCracking 对象可以具有以下成员：

*brittleShear*

一个 [BrittleShear](pt01ch29pyo07.md) 对象。

*brittleFailure*

一个 [BrittleFailure](pt01ch29pyo06.md) 对象。

### 29.5.4 对应的分析关键字

| [*BRITTLE CRACKING](../key/key-link.md#usb-kws-mcracking) |
| --- |




