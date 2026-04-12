# 25.35 FluidCavityProperty 对象

FluidCavityProperty 对象是交互属性，定义基于表面流体腔体的流体行为。

FluidCavityProperty 对象派生自 [InteractionProperty](pt01ch25pyo48.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.35.1 FluidCavityProperty(...)

此方法创建一个 FluidCavityProperty 对象。

**路径**

```
mdb.models[*name*].FluidCavityProperty
```

**必需参数**

*name*

字符串，指定交互属性存储库键。

**可选参数**

*definition*

 SymbolicConstant，指定要定义的流体腔体属性类型。可能的值为 HYDRAULIC 和 PNEUMATIC。默认值为 HYDRAULIC。

*fluidDensity*

 `None` 或浮点数，指定参考流体密度。此参数仅在 *definition*=HYDRAULIC 时适用，并且在那种情况下是必需的。默认值为 `None`。

*molecularWeight*

 `None` 或浮点数，指定理想气体物种的分子量。此参数仅在 *definition*=PNEUMATIC 时适用，并且在那种情况下是必需的。默认值为 `None`。

*useExpansion*

布尔值，指定是否定义热膨胀系数。此参数仅在 *definition*=HYDRAULIC 时适用。默认值为 OFF。

*expansionTempDep*

布尔值，指定热流体膨胀数据是否具有温度依赖性。此参数仅在 *definition*=HYDRAULIC 且 *useExpansion*=True 时适用。默认值为 OFF。

*expansionDependencies*

整数，指定热流体膨胀数据中的场变量依赖项数量。此参数仅在 *definition*=HYDRAULIC 且 *useExpansion*=True 时适用。默认值为 0。

*referenceTemperature*

浮点数，指定热膨胀系数的参考温度。此参数仅在 *definition*=HYDRAULIC、*useExpansion*=True 且 *expansionTempDep*=True 或 *expansionDependencies* 大于 0 时适用。默认值为 0.0。

*expansionTable*

浮点数序列的序列，指定热膨胀系数。此参数仅在 *definition*=HYDRAULIC 且 *useExpansion*=True 时适用。每个序列包含以下数据：
- 平均热膨胀系数。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

*useBulkModulus*

布尔值，指定是否定义流体体积模量值。此参数仅在 *definition*=HYDRAULIC 时适用。默认值为 OFF。

*bulkModulusTempDep*

布尔值，指定流体体积模量数据是否具有温度依赖性。此参数仅在 *definition*=HYDRAULIC 且 *useBulkModulus*=True 时适用。默认值为 OFF。

*bulkModulusDependencies*

整数，指定流体体积模量数据中的场变量依赖项数量。此参数仅在 *definition*=HYDRAULIC 且 *useBulkModulus*=True 时适用。默认值为 0。

*bulkModulusTable*

浮点数序列的序列，指定流体体积模量值。此参数仅在 *definition*=HYDRAULIC 且 *useBulkModulus*=True 时适用。每个序列包含以下数据：
- 流体体积模量。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

*useCapacity*

布尔值，指定是否定义摩尔热容值。此参数仅在 *definition*=PNEUMATIC 时适用。默认值为 OFF。

*capacityType*

 SymbolicConstant，指定定义摩尔热容的方法。可能的值为 POLYNOMIAL 和 TABULAR。默认值为 POLYNOMIAL。

*capacityTempDep*

布尔值，指定摩尔热容数据是否具有温度依赖性。此参数仅在 *definition*=PNEUMATIC、*useCapacity*=True 且 *capacityType*=TABULAR 时适用。默认值为 OFF。

*capacityDependencies*

整数，指定摩尔热容数据中的场变量依赖项数量。此参数仅在 *definition*=PNEUMATIC、*useCapacity*=True 且 *capacityType*=TABULAR 时适用。默认值为 0。

*capacityTable*

浮点数序列的序列，以多项式表达式的形式指定摩尔热容值。此参数仅在 *definition*=PNEUMATIC、*useCapacity*=True 且 *capacityType*=POLYNOMIAL 时适用。在这种形式中，只指定一个序列，该序列包含以下数据：
- 第一个摩尔热容系数。
- 第二个摩尔热容系数。
- 第三个摩尔热容系数。
- 第四个摩尔热容系数。
- 第五个摩尔热容系数。

或者，序列数据可以指定理想气体物种在恒压下的摩尔热容。此参数仅在 *definition*=PNEUMATIC、*useCapacity*=True 且 *capacityType*=TABULAR 时适用。每个序列包含以下数据：
- 恒压摩尔热容。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 依此类推。

**返回值**

FluidCavityProperty 对象。

**异常**

无。

### 25.35.2 setValues(...)

此方法修改 FluidCavityProperty 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [FluidCavityProperty](pt01ch25pyo35.md#ker-fluidcavityproperty-fluidcavityproperty-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 25.35.3 成员

FluidCavityProperty 对象的成员与 [FluidCavityProperty](pt01ch25pyo35.md#ker-fluidcavityproperty-fluidcavityproperty-pyc) 方法的参数具有相同的名称和描述。

### 25.35.4 对应的分析关键字

| [*FLUID BEHAVIOR](../key/key-link.md#usb-kws-mfluidbehavior) |
| --- |
| [*CAPACITY](../key/key-link.md#usb-kws-mcapacity) |
| [*FLUID BULK MODULUS](../key/key-link.md#usb-kws-mfluidbulk) |
| [*FLUID DENSITY](../key/key-link.md#usb-kws-mfluiddensity) |
| [*FLUID EXPANSION](../key/key-link.md#usb-kws-mfluidexpansion) |
| [*MOLECULAR WEIGHT](../key/key-link.md#usb-kws-mmolecularweight) |



