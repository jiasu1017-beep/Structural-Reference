# 29.47 Eos 对象

Eos 对象指定状态方程模型。

**访问**

```
import material
mdb.models[*name*].materials[*name*].eos
import odbMaterial
session.odbs[*name*].materials[*name*].eos
```

### 29.47.1 Eos(...)

此方法创建 Eos 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Eos
session.odbs[*name*].materials[*name*].Eos
```

**必需参数**

无。

**可选参数**

*type*

 SymbolicConstant，指定状态方程。可能的值为 USUP、JWL、IDEALGAS、TABULAR 和 IGNITIONANDGROWTH。默认值为 IDEALGAS。

*temperatureDependency*

 Boolean，指定 *gasSpecificTable* 中的数据是否依赖于温度。默认值为 OFF。

*dependencies*

 Int，指定 *gasSpecificTable* 中数据的场变量依赖项数量。默认值为 0。

*detonationEnergy*

 Float，指定起爆能量文本字段。默认值为 0.0。

*solidTable*

 Float 元组序列，指定以下内容：
- $A_{s}$。
- $B_{s}$。
- ${\omega}_{s}$。
- $R_{1s}$。
- $R_{2s}$。

默认值为空序列。

*gasTable*

 Float 元组序列，指定以下内容：
- $A_{g}$。
- $B_{g}$。
- ${\omega}_{g}$。
- $R_{1g}$。
- $R_{2g}$。

默认值为空序列。

*reactionTable*

 Float 元组序列，指定以下内容：
- 初始压力，$I$。
- 产物比容，$a$。
- 未反应分数的指数（点燃项），$x$。
- 第一燃速系数，$G_{1}$
- 未反应分数的指数（增长项），$c$。
- 反应分数的指数（增长项），$d$。
- 压力指数（增长项），$y$。
- 第二燃速系数，$G_{2}$。
- 未反应分数的指数（完成项），$e$。
- 反应分数的指数（完成项），$g$。
- 压力指数（完成项），$z$。
- 初始反应分数，${F^{max}}_{ig}$。
- 增长项的最大反应分数，${F^{max}}_{G1}$。
- 最小反应分数，${F^{min}}_{G2}$。

默认值为空序列。

*gasSpecificTable*

 Float 元组序列，指定以下内容：
- 每单位质量比热容。
- 温度依赖数据。
- 第一个场变量的值。
- 第二个场变量的值。
- 以此类推。

默认值为空序列。

*table*

 Float 元组序列，指定下述项目。默认值为空序列。

**表格数据**

如果 *type*=IDEALGAS，表格数据表示以下内容：
- 气体常数，![](../graphics/ker_eqn00096.gif)。
- 环境压力，![](../graphics/ker_eqn00227.gif)。如果此字段留空，则使用默认值 0.0。

如果 *type*=JWL，表格数据表示以下内容：
- 起爆波速度，![](../graphics/ker_eqn00228.gif)。
- ![](../graphics/ker_eqn00010.gif)。
- ![](../graphics/ker_eqn00150.gif)。
- ![](../graphics/ker_eqn00016.gif)。（无量纲。）
- ![](../graphics/ker_eqn00229.gif)。（无量纲。）
- ![](../graphics/ker_eqn00230.gif)。（无量纲。）
- 预起爆体模量，![](../graphics/ker_eqn00231.gif)。
- 起爆能量密度，![](../graphics/ker_eqn00232.gif)。

如果 *type*=USUP，表格数据表示以下内容：
- ![](../graphics/ker_eqn00233.gif)。
- ![](../graphics/ker_eqn00234.gif)。（无量纲。）
- ![](../graphics/ker_eqn00235.gif)。（无量纲。）

如果 *type*=TABULAR，表格数据表示以下内容：
- ![](../graphics/ker_eqn00236.gif)。
- ![](../graphics/ker_eqn00237.gif)。
- ![](../graphics/ker_eqn00238.gif)。（无量纲。）

**返回值**

 Eos 对象。

**异常**

无。

### 29.47.2 setValues(...)

此方法修改 Eos 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [Eos](pt01ch29pyo47.md#ker-eos-eos-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 29.47.3 成员

Eos 对象的成员与 [Eos](pt01ch29pyo47.md#ker-eos-eos-pyc) 方法的参数具有相同的名称和描述。

此外，Eos 对象可以具有以下成员：

*detonationPoint*

 [DetonationPoint](pt01ch29pyo39.md) 对象。

*eosCompaction*

 [EosCompaction](pt01ch29pyo48.md) 对象。

### 29.47.4 对应的分析关键字

| [*EOS](../key/key-link.md#usb-kws-meos) |
| --- |
