# 25.38 FluidExchangeProperty 对象

FluidExchangeProperty 对象是定义两个流体腔之间或流体腔与其环境之间流动的流体交换属性的交互属性。

FluidExchangeProperty 对象派生自 [InteractionProperty](pt01ch25pyo48.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.38.1 FluidExchangeProperty(...)

此方法创建 FluidExchangeProperty 对象。

**路径**

```
mdb.models[*name*].FluidExchangeProperty
```

**必需参数**

*name*

String，指定交互属性存储库密钥。

*dataTable*

Float 序列的序列，指定粘性和水动力阻力系数（当 *definition*=BULK_VISCOSITY 时）。每个序列包含以下数据：
- 粘性阻力系数。
- 水动力阻力系数。
- 平均绝对压力（如果数据依赖于压力）。
- 平均温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

或者，序列数据可以指定质量流率。这仅在 *definition*=MASS_FLUX 时适用。在这种情况下，只指定一个序列，该序列包含以下数据：
- 单位面积质量流率。

或者，序列数据可以指定质量泄漏率。这仅在 *definition*=MASS_RATE_LEAK 时适用。每个序列包含以下数据：
- 单位面积质量流率的绝对值。（输入的第一个表值必须始终为零。）
- 压力差的绝对值。（输入的第一个表值必须始终为零。）
- 平均绝对压力（如果数据依赖于压力）。
- 平均温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

或者，序列数据可以指定体积流率。这仅在 *definition*=VOL_FLUX 时适用。在这种情况下，只指定一个序列，该序列包含以下数据：
- 单位面积体积流率。

或者，序列数据可以指定体积泄漏率。这仅在 *definition*=VOL_RATE_LEAK 时适用。每个序列包含以下数据：
- 单位面积体积流率的绝对值。（输入的第一个表值必须始终为零。）
- 压力差的绝对值。（输入的第一个表值必须始终为零。）
- 平均绝对压力（如果数据依赖于压力）。
- 平均温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**可选参数**

*definition*

SymbolicConstant，指定要定义的流体交换属性类型。可能的值为 BULK_VISCOSITY、MASS_FLUX、MASS_RATE_LEAK、VOL_FLUX 和 VOL_RATE_LEAK。默认值为 BULK_VISCOSITY。

*pressureDependency*

布尔值，指定数据是否具有压力依赖性。此参数仅在 *definition*=BULK_VISCOSITY、*definition*=MASS_RATE_LEAK 或 *definition*=VOL_RATE_LEAK 时适用。默认值为 OFF。

*temperatureDependency*

布尔值，指定数据是否具有温度依赖性。此参数仅在 *definition*=BULK_VISCOSITY、*definition*=MASS_RATE_LEAK 或 *definition*=VOL_RATE_LEAK 时适用。默认值为 OFF。

*fieldDependencies*

Int，指定数据中场变量依赖项的数量。此参数仅在 *definition*=BULK_VISCOSITY、*definition*=MASS_RATE_LEAK 或 *definition*=VOL_RATE_LEAK 时适用。默认值为 0。

**返回值**

FluidExchangeProperty 对象。

**异常**

无。

### 25.38.2 setValues(...)

此方法修改 FluidExchangeProperty 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [FluidExchangeProperty](pt01ch25pyo38.md#ker-fluidexchangeproperty-fluidexchangeproperty-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 25.38.3 成员

FluidExchangeProperty 对象的成员与 [FluidExchangeProperty](pt01ch25pyo38.md#ker-fluidexchangeproperty-fluidexchangeproperty-pyc) 方法的参数具有相同的名称和描述。

### 25.38.4 对应的分析关键字

| [*FLUID EXCHANGE PROPERTY](../key/key-link.md#usb-kws-mfluidexchangeprop) |
| --- |
