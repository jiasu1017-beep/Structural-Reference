# 29.32 DamageInitiation 对象





DamageInitiation 对象指定用于定义损伤起始的材料属性。

**访问**

```
import material
mdb.models[*name*].materials[*name*].ductileDamageInitiation
mdb.models[*name*].materials[*name*].fldDamageInitiation
mdb.models[*name*].materials[*name*].flsdDamageInitiation
mdb.models[*name*].materials[*name*].hashinDamageInitiation
mdb.models[*name*].materials[*name*].johnsonCookDamageInitiation
mdb.models[*name*].materials[*name*].maxeDamageInitiation
mdb.models[*name*].materials[*name*].maxpeDamageInitiation
mdb.models[*name*].materials[*name*].maxpsDamageInitiation
mdb.models[*name*].materials[*name*].maxsDamageInitiation
mdb.models[*name*].materials[*name*].mkDamageInitiation
mdb.models[*name*].materials[*name*].msfldDamageInitiation
mdb.models[*name*].materials[*name*].quadeDamageInitiation
mdb.models[*name*].materials[*name*].quadsDamageInitiation
mdb.models[*name*].materials[*name*].shearDamageInitiation
import odbMaterial
session.odbs[*name*].materials[*name*].ductileDamageInitiation
session.odbs[*name*].materials[*name*].fldDamageInitiation
session.odbs[*name*].materials[*name*].flsdDamageInitiation
session.odbs[*name*].materials[*name*].hashinDamageInitiation
session.odbs[*name*].materials[*name*].johnsonCookDamageInitiation
session.odbs[*name*].materials[*name*].maxeDamageInitiation
session.odbs[*name*].materials[*name*].maxpeDamageInitiation
session.odbs[*name*].materials[*name*].maxpsDamageInitiation
session.odbs[*name*].materials[*name*].maxsDamageInitiation
session.odbs[*name*].materials[*name*].mkDamageInitiation
session.odbs[*name*].materials[*name*].msfldDamageInitiation
session.odbs[*name*].materials[*name*].quadeDamageInitiation
session.odbs[*name*].materials[*name*].quadsDamageInitiation
session.odbs[*name*].materials[*name*].shearDamageInitiation
```

### 29.32.1 DuctileDamageInitiation(...)

此方法创建 DamageInitiation 对象。

**路径**

```
mdb.models[*name*].materials[*name*].DuctileDamageInitiation
session.odbs[*name*].materials[*name*].DuctileDamageInitiation
```

**必需参数**

*table*

一个 Float 元组序列，指定"表格数据"部分中描述的项目。

**可选参数**

*definition*

一个 SymbolicConstant，指定损伤起始定义。可能的值为 FLD 和 MSFLD。默认值为 MSFLD。

*feq*

一个 Float，指定等效塑性应变变形严重度指数的临界值。默认值为 10.0。

*fnn*

一个 Float，指定垂直于沟槽方向应变变形严重度指数的临界值。默认值为 10.0。

*fnt*

一个 Float，指定剪切应变变形严重度指数的临界值。默认值为 10.0。

*frequency*

一个 Int，指定执行 Marciniak-Kuczynski 分析的频率（增量数）。默认值为 1。

*ks*

一个 Float，指定 Ks 的值。默认值为 0.0。

*numberImperfections*

一个 Int，指定在评估 Marciniak-Kuczynski 分析时要考虑的缺陷数量。这些缺陷假定在角方向上等距分布。默认值为 4。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖项的数量。默认值为 0。

*alpha*

一个 Float，指定将乘以 Hashin 纤维起始准则中剪切贡献的系数值。默认值为 0.0。

*omega*

一个 Float，指定用于过滤用于评估 MSFLD 损伤起始准则的主应变率比的过滤因子。默认值为 1.0。

*tolerance*

一个 Float，指定损伤起始准则必须满足的容差。默认值为 0.05。

*direction*

一个 SymbolicConstant，指定损伤起始方向。可能的值为 NMORI 和 TMORI。默认值为 NMORI。

**表格数据**

如果构造函数为 `DuctileDamageInitiation`，表格数据指定以下内容：
- 损伤起始时的等效断裂应变。
- 应力三轴度。
- 应变率。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `FldDamageInitiation`，表格数据指定以下内容：
- 损伤起始时的主应变。
- 次应变。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `FlsdDamageInitiation`，表格数据指定以下内容：
- 损伤起始时的主应力。
- 次应力。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `JohnsonCookDamageInitiation`，表格数据指定以下内容：
- Johnson-Cook 失效参数 D1。
- Johnson-Cook 失效参数 D2。
- Johnson-Cook 失效参数 D3。
- Johnson-Cook 失效参数 D4。
- Johnson-Cook 失效参数 D5。
- 熔化温度。
- 转变温度。
- 参考应变率。

如果构造函数为 `MkDamageInitiation`，表格数据指定以下内容：
- 相对于截面公称厚度的缺陷大小。
- 相对于局部材料方向 1 方向的角度（度）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `MsfldDamageInitiation` 且 *definition*=MSFLD，表格数据指定以下内容：
- 仅法向模式时损伤起始的公称应变。
- 局部颈化起始时的等效塑性应变。
- 次应变与主应变之比。
- 等效塑性应变率。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `MsfldDamageInitiation` 且 *definition*=FLD，表格数据指定以下内容：
- 局部颈化起始时的主应变。
- 局部颈化起始时的等效塑性应变。
- 次应变与主应变之比。
- 等效塑性应变率。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `QuadeDamageInitiation` 或 `MaxeDamageInitiation`，表格数据指定以下内容：
- 仅法向模式时损伤起始的公称应变。
- 仅沿第一个剪切方向分离的剪切模式时损伤起始的公称应变。
- 仅沿第二个剪切方向分离的剪切模式时损伤起始的公称应变。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `QuadsDamageInitiation` 或 `MaxsDamageInitiation`，表格数据指定以下内容：
- 仅法向模式时损伤起始的公称应变。
- 仅沿第一个剪切方向分离的剪切模式时损伤起始的公称应变。
- 仅沿第二个剪切方向分离的剪切模式时损伤起始的公称应变。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `MaxpeDamageInitiation`，表格数据指定以下内容：
- 损伤起始时的最大主应变。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `MaxpsDamageInitiation`，表格数据指定以下内容：
- 损伤起始时的最大主应力。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `ShearDamageInitiation`，表格数据指定以下内容：
- 损伤起始时的等效断裂应变。
- 剪切应力比。
- 应变率。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果构造函数为 `HashinDamageInitiation`，表格数据指定以下内容：
- 纤维拉伸强度。
- 纤维压缩强度。
- 基体拉伸强度。
- 基体压缩强度。
- 纵向剪切强度。
- 横向剪切强度。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

一个 DamageInitiation 对象。

**异常**

RangeError。

### 29.32.2 setValues(...)

此方法修改 DamageInitiation 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DamageInitiation](pt01ch29pyo32.md#ker-damageinitiation-ductiledamageinitiation-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.32.3 成员

DamageInitiation 对象可以具有以下成员：

*definition*

一个 SymbolicConstant，指定损伤起始定义。可能的值为 FLD 和 MSFLD。默认值为 MSFLD。

*feq*

一个 Float，指定等效塑性应变变形严重度指数的临界值。默认值为 10.0。

*fnn*

一个 Float，指定垂直于沟槽方向应变变形严重度指数的临界值。默认值为 10.0。

*fnt*

一个 Float，指定剪切应变变形严重度指数的临界值。默认值为 10.0。

*frequency*

一个 Int，指定执行 Marciniak-Kuczynski 分析的频率（增量数）。默认值为 1。

*ks*

一个 Float，指定 Ks 的值。默认值为 0.0。

*numberImperfections*

一个 Int，指定在评估 Marciniak-Kuczynski 分析时要考虑的缺陷数量。这些缺陷假定在角方向上等距分布。默认值为 4。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 OFF。

*dependencies*

一个 Int，指定场变量依赖项的数量。默认值为 0。

*alpha*

一个 Float，指定将乘以 Hashin 纤维起始准则中剪切贡献的系数值。默认值为 0.0。

*omega*

一个 Float，指定用于过滤用于评估 MSFLD 损伤起始准则的主应变率比的过滤因子。默认值为 1.0。

*tolerance*

一个 Float，指定损伤起始准则必须满足的容差。默认值为 0.05。

*direction*

一个 SymbolicConstant，指定损伤起始方向。可能的值为 NMORI 和 TMORI。默认值为 NMORI。

*table*

一个 Float 元组元组，指定"表格数据"部分中描述的项目。

*damageEvolution*

一个 [DamageEvolution](pt01ch29pyo31.md) 对象。

*damageStabilization*

一个 [DamageStabilization](pt01ch29pyo33.md) 对象。

*damageStabilizationCohesive*

一个 [DamageStabilizationCohesive](pt01ch29pyo34.md) 对象。

### 29.32.4 对应的分析关键字

| [*DAMAGE INITIATION](../key/key-link.md#usb-kws-mdamageinitiation) |
| --- |




