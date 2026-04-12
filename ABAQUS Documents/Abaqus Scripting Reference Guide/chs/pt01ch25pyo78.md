# 25.78 ThermalConductance 对象

ThermalConductance 对象为接触交互属性指定热导。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].thermalConductance
```

### 25.78.1 ThermalConductance(...)

此方法创建一个 ThermalConductance 对象。

**路径**

```
mdb.models[*name*].interactionProperties[*name*].ThermalConductance
```

**必需参数**

无。

**可选参数**

*definition*

 SymbolicConstant，指定如何定义热导。可能的值为 TABULAR 和 USER_DEFINED。默认值为 TABULAR。

*clearanceDependency*

布尔值，指定是否使用间隙依赖数据。默认值为 ON。

*pressureDependency*

布尔值，指定是否使用压力依赖数据。默认值为 OFF。

*temperatureDependencyC*

布尔值，指定是否使用具有间隙依赖的温度依赖数据。默认值为 OFF。

*massFlowRateDependencyC*

布尔值，指定是否使用具有间隙依赖的质量流率依赖数据。默认值为 OFF。

*dependenciesC*

整数，指定与间隙依赖一起使用的场变量数量。默认值为 0。

*clearanceDepTable*

浮点数序列的序列，指定间隙依赖数据。表格数据中的项目在下面描述。

*temperatureDependencyP*

布尔值，指定是否使用具有压力依赖的温度依赖数据。默认值为 OFF。

*massFlowRateDependencyP*

布尔值，指定是否使用具有压力依赖的质量流率依赖数据。默认值为 OFF。

*dependenciesP*

整数，指定与压力依赖一起使用的场变量数量。默认值为 0。

*pressureDepTable*

浮点数序列的序列，指定压力依赖数据。表格数据中的项目在下面描述。

**表格数据**

*clearanceDepTable* 数据指定以下内容：
- 电导率。
- 间隙。
- 温度（如果数据依赖于温度）。
- 质量流率（如果数据依赖于质量流率）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

*pressureDepTable* 数据指定以下内容：
- 电导率。
- 压力。
- 温度（如果数据依赖于温度）。
- 质量流率（如果数据依赖于质量流率）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

ThermalConductance 对象。

**异常**

无。

### 25.78.2 setValues(...)

此方法修改 ThermalConductance 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ThermalConductance](pt01ch25pyo78.md#ker-thermalconductance-thermalconductance-pyc) 方法的参数相同。

**返回值**

无。

**异常**

无。

### 25.78.3 成员

ThermalConductance 对象的成员与 [ThermalConductance](pt01ch25pyo78.md#ker-thermalconductance-thermalconductance-pyc) 方法的参数具有相同的名称和描述。

### 25.78.4 对应的分析关键字

| [*GAP CONDUCTANCE](../key/key-link.md#usb-kws-mgapconduct) |
| --- |



