# 25.17 ContactDamage 对象

ContactDamage 对象为接触交互属性指定损伤选项。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].damage
```

### 25.17.1 Damage(...)

此方法创建一个 ContactDamage 对象。

**路径**

```
mdb.models[*name*].interactionProperties[*name*].Damage
```

**必需参数**

*initTable*

浮点数序列的序列，指定定义损伤起始的值。表格数据中的项目在下面描述。

**可选参数**

*criterion*

 SymbolicConstant，指定用于定义损伤起始的数据类型。可能的值为 MAX_STRESS、MAX_SEPARATION、QUAD_TRACTION 和 QUAD_SEPARATION。默认值为 MAX_STRESS。

*initTempDep*

布尔值，指定起始数据是否依赖于温度。默认值为 OFF。

*initDependencies*

整数，指定起始数据场变量的数量。默认值为 0。

*useEvolution*

布尔值，指定是否定义演化数据。默认值为 OFF。

*evolutionType*

 SymbolicConstant，指定用于定义损伤演化的数据类型。此参数仅在 *useEvolution*=ON 时有效。可能的值为 DISPLACEMENT 和 ENERGY。默认值为 DISPLACEMENT。

*softening*

 SymbolicConstant，指定用于定义演化软化响应的数据类型。此参数仅在 *useEvolution*=ON 时有效。TABULAR 值仅在 *evolutionType*=DISPLACEMENT 时可用。可能的值为 LINEAR、EXPONENTIAL 和 TABULAR。默认值为 LINEAR。

*useMixedMode*

布尔值，指定是否使用从属行为模式定义演化数据。此参数仅在 *useEvolution*=ON 时有效。默认值为 OFF。

*mixedModeType*

 SymbolicConstant，指定模式混合断裂准则。此参数仅在 *useEvolution*=ON 且 *useMixedMode*=ON 时有效。POWER_LAW 和 BK 值仅在 *evolutionType*=ENERGY 时可用。可能的值为 TABULAR、POWER_LAW 和 BK。默认值为 TABULAR。

*modeMixRatio*

 SymbolicConstant，指定模式混合比类型。此参数仅在 *useEvolution*=ON 且 *useMixedMode*=ON 时有效。TRACTION 值仅在 *mixedModeType*=TABULAR 时可用。可能的值为 ENERGY 和 TRACTION。默认值为 ENERGY。

*exponent*

 `None` 或浮点数，指定功率律或 BK 准则中定义断裂能随模式混合变化的指数。此参数仅在 *useEvolution*=ON 且 *mixedModeType*=POWER_LAW 或 BK 时有效。默认值为 `None`。

*evolTempDep*

布尔值，指定演化数据是否依赖于温度。此参数仅在 *useEvolution*=ON 时有效。默认值为 OFF。

*evolDependencies*

整数，指定演化数据场变量的数量。此参数仅在 *useEvolution*=ON 时有效。默认值为 0。

*evolTable*

浮点数序列的序列，指定定义损伤演化的值。表格数据中的项目在下面描述。此参数仅在 *useEvolution*=ON 时有效。

*useStabilization*

布尔值，指定是否定义稳定化数据。此参数仅在 *useEvolution*=ON 时有效。默认值为 OFF。

*viscosityCoef*

 `None` 或浮点数，指定粘度系数。此参数仅在 *useStabilization*=ON 时有效。默认值为 `None`。

**表格数据**

*initTable* 的表格数据：

如果 *criterion*=MAX_STRESS 或 QUAD_TRACTION，表格数据指定以下内容：
- 纯法向模式下的最大名义应力。
- 第一个剪切方向（对于仅涉及该方向分离的模式）的最大名义应力。
- 第二个剪切方向（对于仅涉及该方向分离的模式）的最大名义应力。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *criterion*=MAX_SEPARATION 或 QUAD_SEPARATION，表格数据指定以下内容：
- 法向模式下损伤起始时的分离量。
- 剪切模式下损伤起始时的分离量（仅涉及沿第一个剪切方向的分离）。
- 剪切模式下损伤起始时的分离量（仅涉及沿第二个剪切方向的分离）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

*evolTable* 的表格数据：

如果 *evolutionType*=DISPLACEMENT、*softening*=LINEAR 且 *useMixedMode*=OFF，表格数据指定以下内容：
- 从损伤起始时刻起的有效总位移或塑性位移失效。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=ENERGY、*softening*=LINEAR 或 EXPONENTIAL 且 *useMixedMode*=OFF，表格数据指定以下内容：
- 断裂能。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=DISPLACEMENT、*softening*=LINEAR、*useMixedMode*=ON、*mixedModeType*=TABULAR 且 *modeMixRatio*=ENERGY 或 TRACTION，表格数据指定以下内容：
- 从损伤起始时刻起的总位移失效。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。

如果 *evolutionType*=ENERGY、*softening*=LINEAR 或 EXPONENTIAL、*useMixedMode*=ON、*mixedModeType*=TABULAR 且 *modeMixRatio*=ENERGY 或 TRACTION，表格数据指定以下内容：
- 断裂能。
- 适当的模式混合比。
- 适当的模式混合比（如果相关）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=DISPLACEMENT、*softening*=EXPONENTIAL 且 *useMixedMode*=OFF，表格数据指定以下内容：
- 从损伤起始时刻起的有效总位移或塑性位移失效。
- 指数律参数。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=DISPLACEMENT、*softening*=EXPONENTIAL、*useMixedMode*=ON、*mixedModeType*=TABULAR 且 *modeMixRatio*=ENERGY 或 TRACTION，表格数据指定以下内容：
- 从损伤起始时刻起的总位移失效。
- 指数律参数。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=DISPLACEMENT、*softening*=TABULAR 且 *useMixedMode*=OFF，表格数据指定以下内容：
- 损伤变量。
- 从损伤起始时刻起的有效总位移或塑性位移失效。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=DISPLACEMENT、*softening*=TABULAR、*useMixedMode*=ON、*mixedModeType*=TABULAR 且 *modeMixRatio*=ENERGY 或 TRACTION，表格数据指定以下内容：
- 损伤变量。
- 从损伤起始时刻起的有效总位移。
- 适当的模式混合比。
- 适当的模式混合比（如果与各向异性剪切行为的三维问题相关）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

如果 *evolutionType*=ENERGY、*softening*=LINEAR 或 EXPONENTIAL、*useMixedMode*=ON、*mixedModeType*=POWER_LAW 或 BK 且 *modeMixRatio*=ENERGY，表格数据指定以下内容：
- 法向模式断裂能。
- 第一个剪切方向失效的剪切模式断裂能。
- 第二个剪切方向失效的剪切模式断裂能。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

ContactDamage 对象。

**异常**

无。

### 25.17.2 setValues(...)

此方法修改 ContactDamage 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ContactDamage](pt01ch25pyo17.md#ker-contactdamage-damage-pyc) 方法的参数相同。

**返回值**

无。

**异常**

无。

### 25.17.3 成员

ContactDamage 对象具有以下成员：

*criterion*

 SymbolicConstant，指定用于定义损伤起始的数据类型。可能的值为 MAX_STRESS、MAX_SEPARATION、QUAD_TRACTION 和 QUAD_SEPARATION。默认值为 MAX_STRESS。

*initTempDep*

布尔值，指定起始数据是否依赖于温度。默认值为 OFF。

*initDependencies*

整数，指定起始数据场变量的数量。默认值为 0。

*useEvolution*

布尔值，指定是否定义演化数据。默认值为 OFF。

*evolutionType*

 SymbolicConstant，指定用于定义损伤演化的数据类型。此参数仅在 *useEvolution*=ON 时有效。可能的值为 DISPLACEMENT 和 ENERGY。默认值为 DISPLACEMENT。

*softening*

 SymbolicConstant，指定用于定义演化软化响应的数据类型。此参数仅在 *useEvolution*=ON 时有效。TABULAR 值仅在 *evolutionType*=DISPLACEMENT 时可用。可能的值为 LINEAR、EXPONENTIAL 和 TABULAR。默认值为 LINEAR。

*useMixedMode*

布尔值，指定是否使用从属行为模式定义演化数据。此参数仅在 *useEvolution*=ON 时有效。默认值为 OFF。

*mixedModeType*

 SymbolicConstant，指定模式混合断裂准则。此参数仅在 *useEvolution*=ON 且 *useMixedMode*=ON 时有效。POWER_LAW 和 BK 值仅在 *evolutionType*=ENERGY 时可用。可能的值为 TABULAR、POWER_LAW 和 BK。默认值为 TABULAR。

*modeMixRatio*

 SymbolicConstant，指定模式混合比类型。此参数仅在 *useEvolution*=ON 且 *useMixedMode*=ON 时有效。TRACTION 值仅在 *mixedModeType*=TABULAR 时可用。可能的值为 ENERGY 和 TRACTION。默认值为 ENERGY。

*exponent*

 `None` 或浮点数，指定功率律或 BK 准则中定义断裂能随模式混合变化的指数。此参数仅在 *useEvolution*=ON 且 *mixedModeType*=POWER_LAW 或 BK 时有效。默认值为 `None`。

*evolTempDep*

布尔值，指定演化数据是否依赖于温度。此参数仅在 *useEvolution*=ON 时有效。默认值为 OFF。

*evolDependencies*

整数，指定演化数据场变量的数量。此参数仅在 *useEvolution*=ON 时有效。默认值为 0。

*useStabilization*

布尔值，指定是否定义稳定化数据。此参数仅在 *useEvolution*=ON 时有效。默认值为 OFF。

*viscosityCoef*

 `None` 或浮点数，指定粘度系数。此参数仅在 *useStabilization*=ON 时有效。默认值为 `None`。

*initTable*

浮点数元组的元组，指定定义损伤起始的值。表格数据中的项目在下面描述。

*evolTable*

浮点数元组的元组，指定定义损伤演化的值。表格数据中的项目在下面描述。此参数仅在 *useEvolution*=ON 时有效。

### 25.17.4 对应的分析关键字

| [*DAMAGE INITIATION](../key/key-link.md#usb-kws-mdamageinitiation) |
| --- |
| [*DAMAGE EVOLUTION](../key/key-link.md#usb-kws-mdamageevolution) |
| [*DAMAGE STABILIZATION](../key/key-link.md#usb-kws-mdamagestabilization) |



