# 60.47 Eos 对象

Eos 对象用于指定状态方程模型。

**访问**

```
materialApi.materials()[*name*].eos()
```

### 60.47.1 Eos(...)

此方法创建一个 Eos 对象。

**路径**

```
materialApi.materials()[*name*].Eos
```

**原型**

```
odb_Eos&
Eos(const odb_String& type,
    bool temperatureDependency,
    int dependencies,
    double detonationEnergy,
    const odb_SequenceSequenceDouble& solidTable,
    const odb_SequenceSequenceDouble& gasTable,
    const odb_SequenceSequenceDouble& reactionTable,
    const odb_SequenceSequenceDouble& gasSpecificTable,
    const odb_SequenceSequenceDouble& table);
```

**必需参数**

无。

**可选参数**

*type*

一个 odb_String，指定状态方程。可能的值为"USUP"、"JWL"、"IDEALGAS"、"TABULAR"和"IGNITIONANDGROWTH"。默认值为"IDEALGAS"。

*temperatureDependency*

一个布尔值，指定 *gasSpecificTable* 中的数据是否依赖温度。默认值为 false。

*dependencies*

一个整数，指定 *gasSpecificTable* 中数据的场变量依赖数量。默认值为 0。

*detonationEnergy*

一个 Double，指定爆轰能量文本字段。默认值为 0.0。

*solidTable*

一个 odb_SequenceSequenceDouble，指定以下内容：
- $A_{s}$。
- $B_{s}$。
- ${\omega}_{s}$。
- $R_{1s}$。
- $R_{2s}$。

默认值为空序列。

*gasTable*

一个 odb_SequenceSequenceDouble，指定以下内容：
- $A_{g}$。
- $B_{g}$。
- ${\omega}_{g}$。
- $R_{1g}$。
- $R_{2g}$。

默认值为空序列。

*reactionTable*

一个 odb_SequenceSequenceDouble，指定以下内容：
- 初始压力，$I$。
- 产物比容，$a$。
- 未反应分数的指数（点火项），$x$。
- 第一燃烧速率系数，$G_{1}$
- 未反应分数的指数（增长项），$c$。
- 已反应分数的指数（增长项），$d$。
- 压力指数（增长项），$y$。
- 第二燃烧速率系数，$G_{2}$。
- 未反应分数的指数（完成项），$e$。
- 已反应分数的指数（完成项），$g$。
- 压力指数（完成项），$z$。
- 初始已反应分数，${F^{max}}_{ig}$。
- 增长项的最大已反应分数，${F^{max}}_{G1}$。
- 最小已反应分数，${F^{min}}_{G2}$。

默认值为空序列。

*gasSpecificTable*

一个 odb_SequenceSequenceDouble，指定以下内容：
- 单位质量比热容。
- 温度依赖数据。
- 第一个场变量的值。
- 第二个场变量的值。
- 依此类推。

默认值为空序列。

*table*

一个 odb_SequenceSequenceDouble，指定如下所述的项目。默认值为空序列。

**表数据**

如果 *type*=IDEALGAS，表数据表示以下内容：
- 气体常数，![](../graphics/ker_eqn00096.gif]。
- 环境压力，![](../graphics/ker_eqn00227.gif]。如果此字段留空，则使用默认值 0.0。

如果 *type*=JWL，表数据表示以下内容：
- 爆轰波速度，![](../graphics/ker_eqn00228.gif]。
- ![](../graphics/ker_eqn00010.gif]。
- ![](../graphics/ker_eqn00150.gif]。
- ![](../graphics/ker_eqn00016.gif]。（无量纲。）
- ![](../graphics/ker_eqn00229.gif]。（无量纲。）
- ![](../graphics/ker_eqn00230.gif]。（无量纲。）
- 预爆轰体积模量，![](../graphics/ker_eqn00231.gif]。
- 爆轰能量密度，![](../graphics/ker_eqn00232.gif]。

如果 *type*=USUP，表数据表示以下内容：
- ![](../graphics/ker_eqn00233.gif]。
- ![](../graphics/ker_eqn00234.gif]。（无量纲。）
- ![](../graphics/ker_eqn00235.gif]。（无量纲。）

如果 *type*=TABULAR，表数据表示以下内容：
- ![](../graphics/ker_eqn00236.gif]。
- ![](../graphics/ker_eqn00237.gif]。
- ![](../graphics/ker_eqn00238.gif]。（无量纲。）

**返回值**

一个 Eos 对象。

**异常**

无。

### 60.47.2 成员

Eos 对象的成员与 [Eos](pt02ch60pyo47.md#ker-eos-eos-cpp) 方法的参数具有相同的名称和描述。

此外，Eos 对象可以具有以下成员：

**原型**

```
odb_DetonationPoint detonationPoint() const;
odb_EosCompaction eosCompaction() const;
```

*detonationPoint*

一个 [DetonationPoint](pt02ch60pyo39.md) 对象。

*eosCompaction*

一个 [EosCompaction](pt02ch60pyo48.md) 对象。

### 60.47.3 对应的分析关键字

| [*EOS](../key/key-link.md#usb-kws-meos) |
| --- |
