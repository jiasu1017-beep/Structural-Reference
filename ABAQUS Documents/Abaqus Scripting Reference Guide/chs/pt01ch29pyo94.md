# 29.94 Sorption 对象

Sorption 对象定义在耦合润湿液体流动和多孔介质应力分析中部分饱和多孔介质的吸收和解吸行为。

**访问**

```
import material
mdb.models[*name*].materials[*name*].sorption
import odbMaterial
session.odbs[*name*].materials[*name*].sorption
```

### 29.94.1 Sorption(...)

此方法创建 Sorption 对象。

**路径**

```
mdb.models[*name*].materials[*name*].Sorption
session.odbs[*name*].materials[*name*].Sorption
```

**必需参数**

*absorptionTable*

Float 元组序列，指定下述项目。

**可选参数**

*lawAbsorption*

SymbolicConstant，指定吸收行为。可能的值为 LOG 和 TABULAR。默认值为 TABULAR。

*exsorption*

Boolean，指定是否指定解吸数据。默认值为 OFF。

*lawExsorption*

SymbolicConstant，指定解吸行为。可能的值为 LOG 和 TABULAR。默认值为 TABULAR。

*scanning*

Float，指定扫描线斜率，![](../graphics/ker_eqn00368.gif)。此斜率必须为正且大于吸收或解吸行为的斜率。默认值为 0.0。

*exsorptionTable*

Float 元组序列，指定下述项目。默认值为空序列。

**表格数据**

如果 *lawAbsorption*=TABULAR 或 *lawExsorption*=TABULAR，则 *absorptionTable* 和 *exsorptionTable* 数据分别指定以下内容：
- 孔隙压力，![](../graphics/ker_eqn00369.gif)。
- 饱和度，![](../graphics/ker_eqn00234.gif)。

如果 *lawAbsorption*=LOG 或 *lawExsorption*=LOG，则 *absorptionTable* 和 *exsorptionTable* 数据分别指定以下内容：
- A。
- B。
- ![](../graphics/ker_eqn00370.gif)。
- ![](../graphics/ker_eqn00371.gif)。

**返回值**

Sorption 对象。

**异常**

RangeError。

### 29.94.2 setValues(...)

此方法修改 Sorption 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [Sorption](pt01ch29pyo94.md#ker-sorption-sorption-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.94.3 成员

Sorption 对象的成员与 [Sorption](pt01ch29pyo94.md#ker-sorption-sorption-pyc) 方法的参数具有相同的名称和描述。

### 29.94.4 对应的分析关键字

| [*SORPTION](../key/key-link.md#usb-kws-msorption) |
| --- |
