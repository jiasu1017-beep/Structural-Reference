# 29.7 BrittleShear 对象





BrittleShear 对象指定脆裂模型中材料的裂后剪切行为。

**访问**

```
import material
mdb.models[*name*].materials[*name*].brittleCracking.brittleShear
import odbMaterial
session.odbs[*name*].materials[*name*].brittleCracking.brittleShear
```

### 29.7.1 BrittleShear(...)

此方法创建 BrittleShear 对象。

**路径**

```
mdb.models[*name*].materials[*name*].brittleCracking.BrittleShear
session.odbs[*name*].materials[*name*].brittleCracking.BrittleShear
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

一个 SymbolicConstant，指定裂后剪切行为的类型。可能的值为 RETENTION_FACTOR 和 POWER_LAW。默认值为 RETENTION_FACTOR。

**表格数据**

如果 *type*=RETENTION_FACTOR，表格数据指定以下内容：
- 剪切保留因子。
- 裂隙张开应变。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=POWER_LAW，表格数据指定以下内容：
- e。
- p。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 BrittleShear 对象。

**异常**

RangeError。

### 29.7.2 setValues(...)

此方法修改 BrittleShear 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [BrittleShear](pt01ch29pyo07.md#ker-brittleshear-brittleshear-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.7.3 成员

BrittleShear 对象具有与 [BrittleShear](pt01ch29pyo07.md#ker-brittleshear-brittleshear-pyc) 方法参数同名的成员，描述也相同。

### 29.7.4 对应的分析关键字

| [*BRITTLE SHEAR](../key/key-link.md#usb-kws-mbrittleshear) |
| --- |




