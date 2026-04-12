# 46.4 BeamSection 对象

BeamSection 对象定义梁截面的属性。

BeamSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.4.1 BeamSection(...)

此方法创建 BeamSection 对象。

**Path**

```
mdb.models[*name*].BeamSection
session.odbs[*name*].BeamSection
```

**必需参数**

*name*

 String，指定存储库键。

*integration*

 SymbolicConstant，指定截面的积分方法。可选值为 BEFORE_ANALYSIS 和 DURING_ANALYSIS。

*profile*

 String，指定轮廓的名称。此参数在 *beamShape*=TAPERED 的情况下表示起始轮廓。

**可选参数**

*poissonRatio*

 Float，指定截面的泊松比。默认值为 0.0。

*thermalExpansion*

 Boolean，指定是否使用热膨胀数据。默认值为 OFF。

*temperatureDependency*

 Boolean，指定数据是否依赖温度。默认值为 OFF。

*dependencies*

 Int，指定场变量依赖项的数量。默认值为 0。

*density*

 `None` 或 Float，指定截面的密度。默认值为 `None`。

*referenceTemperature*

 `None` 或 Float，指定截面的参考温度。默认值为 `None`。

*temperatureVar*

 SymbolicConstant，指定截面的温度变化。可选值为 LINEAR 和 INTERPOLATED。默认值为 LINEAR。

*alphaDamping*

 Float，指定 ![](../graphics/ker_eqn00161.gif) 因子，用于在直接积分动力学中创建质量比例阻尼。默认值为 0.0。

*betaDamping*

 Float，指定 ![](../graphics/ker_eqn00162.gif) 因子，用于在直接积分动力学中创建刚度比例阻尼。默认值为 0.0。

*compositeDamping*

 Float，指定用于在模态动力学中计算复合阻尼因子的临界阻尼分数。默认值为 0.0。

*useFluidInertia*

 Boolean，指定是否模拟附加质量效应。默认值为 OFF。

*submerged*

 SymbolicConstant，指定截面是全淹没还是半淹没。此参数仅在 *useFluidInertia* = True 时适用。可选值为 FULLY 和 HALF。默认值为 FULLY。

*fluidMassDensity*

 `None` 或 Float，指定流体的质量密度。此参数仅在 *useFluidInertia* = True 时适用，必须在这种情况下指定。默认值为 `None`。

*crossSectionRadius*

 `None` 或 Float，指定圆柱截面的半径。此参数仅在 *useFluidInertia* = True 时适用，必须在这种情况下指定。默认值为 `None`。

*lateralMassCoef*

 Float，指定横向运动的附加质量系数 ![](../graphics/ker_eqn00413.gif)。此参数仅在 *useFluidInertia* = True 时适用。默认值为 1.0。

*axialMassCoef*

 Float，指定沿梁轴线运动的附加质量系数 ![](../graphics/ker_eqn00414.gif)。此参数仅影响添加到梁自由端（端部）的项，仅在 *useFluidInertia* = True 时适用。默认值为 0.0。

*massOffsetX*

 Float，指定梁截面圆柱形截面的中心相对于梁截面的局部 1 坐标。此参数仅在 *useFluidInertia* = True 时适用。默认值为 0.0。

*massOffsetY*

 Float，指定梁截面圆柱形截面的中心相对于梁截面的局部 2 坐标。此参数仅在 *useFluidInertia* = True 时适用。默认值为 0.0。

*beamShape*

 SymbolicConstant，指定沿梁长度变化的截面变化。可选值为 CONSTANT 和 TAPERED。默认值为 CONSTANT。此参数可用于操作模型数据库，但不适用于 ODB API。

*material*

 String，指定材料名称。默认值为空字符串。当 *integration* 为 "DURING_ANALYSIS" 时需要材料。

*table*

 Float 序列的序列，指定下述项目。默认值为空序列。

*outputPts*

 Float 对序列，指定请求输出的位置。默认值为空序列。

*centroid*

 Float 对，指定质心的 *X–Y* 坐标。默认值为 (0.0, 0.0)。

*shearCenter*

 Float 对，指定剪切中心的 *X–Y* 坐标。默认值为 (0.0, 0.0)。

*profileEnd*

 String，指定端部轮廓的名称。端部轮廓的类型必须与起始轮廓的类型相同。此参数仅在 *beamShape*=TAPERED 时有效。默认值为空字符串。此参数可用于操作模型数据库，但不适用于 ODB API。

**表数据**

表数据指定以下内容：
- E，截面的杨氏模量。
- G，截面的扭转剪切模量。
- 热膨胀系数（如果使用热膨胀）。
- 温度（如果数据依赖温度）。
- 第一个场变量的值（如果数据依赖场变量）。
- 第二个场变量的值。
- 等等。

**返回值**

BeamSection 对象。

**异常**

无。

### 46.4.2 setValues(...)

此方法修改 BeamSection 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [BeamSection](pt01ch46pyo04.md#ker-beamsection-beamsection-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 46.4.3 成员

BeamSection 对象的成员与 [BeamSection](pt01ch46pyo04.md#ker-beamsection-beamsection-pyc) 方法的参数具有相同的名称和描述。

此外，BeamSection 对象可以具有以下成员：

*beamTransverseShear*

 [TransverseShearBeam](pt01ch46pyo24.md) 对象，指定横向剪切刚度属性。

### 46.4.4 对应分析关键字

| [*BEAM GENERAL SECTION*](../key/key-link.md#usb-kws-mbeamgensect) |
| --- |
| [*BEAM SECTION*](../key/key-link.md#usb-kws-mbeamsection) |
| [*BEAM FLUID INERTIA*](../key/key-link.md#usb-kws-mbeamfluidinertia) |
| [*CENTROID*](../key/key-link.md#usb-kws-mcentroid) |
| [*DAMPING*](../key/key-link.md#usb-kws-mdamping) |
| [*SHEAR CENTER*](../key/key-link.md#usb-kws-mshearcenter) |
| [*SECTION POINTS*](../key/key-link.md#usb-kws-msectionpoints) |

