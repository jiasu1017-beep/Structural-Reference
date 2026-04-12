# 29.31 DamageEvolution 对象





DamageEvolution 对象指定用于定义损伤演化的材料属性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].ductileDamageInitiation\
.damageEvolution
mdb.models[*name*].materials[*name*].fldDamageInitiation.damageEvolution
mdb.models[*name*].materials[*name*].flsdDamageInitiation.damageEvolution
mdb.models[*name*].materials[*name*].hashinDamageInitiation\
.damageEvolution
mdb.models[*name*].materials[*name*].johnsonCookDamageInitiation\
.damageEvolution
mdb.models[*name*].materials[*name*].maxeDamageInitiation.damageEvolution
mdb.models[*name*].materials[*name*].maxpeDamageInitiation.damageEvolution
mdb.models[*name*].materials[*name*].maxpsDamageInitiation.damageEvolution
mdb.models[*name*].materials[*name*].maxsDamageInitiation.damageEvolution
mdb.models[*name*].materials[*name*].mkDamageInitiation.damageEvolution
mdb.models[*name*].materials[*name*].msfldDamageInitiation.damageEvolution
mdb.models[*name*].materials[*name*].quadeDamageInitiation.damageEvolution
mdb.models[*name*].materials[*name*].quadsDamageInitiation.damageEvolution
mdb.models[*name*].materials[*name*].shearDamageInitiation.damageEvolution
import odbMaterial
session.odbs[*name*].materials[*name*].ductileDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].fldDamageInitiation.damageEvolution
session.odbs[*name*].materials[*name*].flsdDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].hashinDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].johnsonCookDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].maxeDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].maxpeDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].maxpsDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].maxsDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].mkDamageInitiation.damageEvolution
session.odbs[*name*].materials[*name*].msfldDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].quadeDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].quadsDamageInitiation\
.damageEvolution
session.odbs[*name*].materials[*name*].shearDamageInitiation\
.damageEvolution
```

### 29.31.1 DamageEvolution(...)

此方法创建 DamageEvolution 对象。

**路径**

```
mdb.models[*name*].materials[*name*].ductileDamageInitiation\
.DamageEvolution
...
```

**必需参数**

*type*

一个 SymbolicConstant，指定损伤演化的类型。可能的值为 DISPLACEMENT 和 ENERGY。

*table*

一个 Float 元组序列，指定如下所述的项目。

**可选参数**

*degradation*

一个 SymbolicConstant，指定退化方式。可能的值为 MAXIMUM 和 MULTIPLICATIVE。默认值为 MAXIMUM。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖项的数量。默认值为 0。

*mixedModeBehavior*

一个 SymbolicConstant，指定混合模式行为。可能的值为 MODE_INDEPENDENT、TABULAR、POWER_LAW 和 BK。默认值为 MODE_INDEPENDENT。

*modeMixRatio*

一个 SymbolicConstant，指定模式混合比。可能的值为 ENERGY 和 TRACTION。默认值为 ENERGY。

*power*

`None` 或一个 Float，指定用于定义相干元素断裂能随模式混合变化的幂律或 Benzeggagh-Kenane 准则的指数。默认值为 `None`。

*softening*

一个 SymbolicConstant，指定软化方式。可能的值为 LINEAR、EXPONENTIAL 和 TABULAR。默认值为 LINEAR。

**表格数据**

如果 *type*=DISPLACEMENT，且 *softening*=LINEAR，且 *mixedModeBehavior*=MODE_INDEPENDENT，表格数据指定以下内容：
- 从损伤起始时刻测量的等效总位移或塑性位移。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，且 *softening*=LINEAR，且 *mixedModeBehavior*=MODE_INDEPENDENT，表格数据指定以下内容：
- 断裂能。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，且 *softening*=LINEAR，且 *mixedModeBehavior*=TABULAR，表格数据指定以下内容：
- 从损伤起始时刻测量的总位移。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，且 *softening*=LINEAR，且 *mixedModeBehavior*=TABULAR，表格数据指定以下内容：
- 断裂能。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，且 *softening*=EXPONENTIAL，且 *mixedModeBehavior*=MODE_INDEPENDENT，表格数据指定以下内容：
- 从损伤起始时刻测量的等效总位移或塑性位移。
- 指数律参数。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，且 *softening*=EXPONENTIAL，且 *mixedModeBehavior*=MODE_INDEPENDENT，表格数据指定以下内容：
- 断裂能。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，且 *softening*=EXPONENTIAL，且 *mixedModeBehavior*=TABULAR，表格数据指定以下内容：
- 从损伤起始时刻测量的总位移。
- 指数律参数。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，且 *softening*=EXPONENTIAL，且 *mixedModeBehavior*=TABULAR，表格数据指定以下内容：
- 断裂能。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，且 *softening*=TABULAR，且 *mixedModeBehavior*=MODE_INDEPENDENT，表格数据指定以下内容：
- 损伤变量。
- 从损伤起始时刻测量的等效总位移或塑性位移。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=DISPLACEMENT，且 *softening*=TABULAR，且 *mixedModeBehavior*=TABULAR，表格数据指定以下内容：
- 损伤变量。
- 从损伤起始时刻测量的等效总位移或塑性位移。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，且 *softening*=LINEAR 或 EXPONENTIAL，且 *mixedModeBehavior*=POWER_LAW 或 BK，表格数据指定以下内容：
- 正模式断裂能。
- 第一个剪切方向断裂的剪切模式断裂能。
- 第二个剪切方向断裂的剪切模式断裂能。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *type*=ENERGY，且 *softening*=LINEAR，且 [DamageInitiation](pt01ch29pyo32.md) 的构造函数为 `HashinDamageInitiation`，表格数据指定以下内容：
- 纤维拉伸断裂能。
- 纤维压缩断裂能。
- 基体拉伸断裂能。
- 基体压缩断裂能。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 DamageEvolution 对象。

**异常**

RangeError。

### 29.31.2 setValues(...)

此方法修改 DamageEvolution 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DamageEvolution](pt01ch29pyo31.md#ker-damageevolution-damageevolution-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.31.3 成员

DamageEvolution 对象具有与 [DamageEvolution](pt01ch29pyo31.md#ker-damageevolution-damageevolution-pyc) 方法参数同名的成员，描述也相同。

### 29.31.4 对应的分析关键字

| [*DAMAGE EVOLUTION](../key/key-link.md#usb-kws-mdamageevolution) |
| --- |




