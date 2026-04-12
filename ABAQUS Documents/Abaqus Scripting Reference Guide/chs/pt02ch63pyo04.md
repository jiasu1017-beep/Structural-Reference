# 63.4 BeamSection 对象

BeamSection 对象定义梁截面的属性。

BeamSection 对象派生自 [Section](pt02ch63pyo01.md) 对象。

**访问**

```
sectionApi.sections()[*name*]
```

### 63.4.1 BeamSection(...)

此方法创建一个 BeamSection 对象。

**路径**

```
sectionApi.BeamSection
```

**原型**

```
odb_BeamSection&
BeamSection(const odb_String& name,
            const odb_String& integration,
            const odb_String& profile,
            double poissonRatio,
            bool thermalExpansion,
            bool temperatureDependency,
            int dependencies,
            odb_Union density,
            odb_Union referenceTemperature,
            const odb_String& temperatureVar,
            double alphaDamping,
            double betaDamping,
            double compositeDamping,
            bool useFluidInertia,
            const odb_String& submerged,
            odb_Union fluidMassDensity,
            odb_Union crossSectionRadius,
            double lateralMassCoef,
            double axialMassCoef,
            double massOffsetX,
            double massOffsetY,            
            const odb_String& material,
            const odb_SequenceSequenceDouble& table,
            const odb_SequenceSequenceDouble& outputPts,
            const odb_SequenceDouble& centroid,
            const odb_SequenceDouble& shearCenter);
```

**必需参数**

*name*

一个 odb_String，指定存储库键。

*integration*

一个 odb_String，指定截面的积分方法。可能的值为 "BEFORE_ANALYSIS" 和 "DURING_ANALYSIS"。

*profile*

一个 odb_String，指定轮廓名称。

**可选参数**

*poissonRatio*

一个 Double，指定截面的泊松比。默认值为 0.0。

*thermalExpansion*

一个 Boolean，指定是否使用热膨胀数据。默认值为 false。

*temperatureDependency*

一个 Boolean，指定数据是否依赖于温度。默认值为 false。

*dependencies*

一个 Int，指定场变量依赖项的数量。默认值为 0。

*density*

字符串 "NONE" 或 Double，指定截面的密度。默认值为 "NONE"。

*referenceTemperature*

字符串 "NONE" 或 Double，指定截面的参考温度。默认值为 "NONE"。

*temperatureVar*

一个 odb_String，指定截面的温度变化。可能的值为 "LINEAR" 和 "INTERPOLATED"。默认值为 "LINEAR"。

*alphaDamping*

一个 Double，指定 ![](../graphics/ker_eqn00161.gif) 因子，用于在直接积分动力学中创建质量比例阻尼。默认值为 0.0。

*betaDamping*

一个 Double，指定 ![](../graphics/ker_eqn00162.gif) 因子，用于在直接积分动力学中创建刚度比例阻尼。默认值为 0.0。

*compositeDamping*

一个 Double，指定用于计算模态复合阻尼因子的临界阻尼分数（用于模态动力学）。默认值为 0.0。

*useFluidInertia*

一个 Boolean，指定是否模拟附加质量效应。默认值为 false。

*submerged*

一个 odb_String，指定截面是完全浸没还是半浸没。此参数仅在 *useFluidInertia* = True 时适用。可能的值为 "FULLY" 和 "HALF"。默认值为 "FULLY"。

*fluidMassDensity*

字符串 "NONE" 或 Double，指定流体的质量密度。此参数仅在 *useFluidInertia* = True 时适用，且在这种情况下必须指定。默认值为 "NONE"。

*crossSectionRadius*

字符串 "NONE" 或 Double，指定圆柱截面的半径。此参数仅在 *useFluidInertia* = True 时适用，且在这种情况下必须指定。默认值为 "NONE"。

*lateralMassCoef*

一个 Double，指定梁横向运动的附加质量系数 ![](../graphics/ker_eqn00413.gif)。此参数仅在 *useFluidInertia* = True 时适用。默认值为 1.0。

*axialMassCoef*

一个 Double，指定沿梁轴线运动的附加质量系数 ![](../graphics/ker_eqn00414.gif)。此参数仅影响添加到梁自由端的项目，且仅在 *useFluidInertia* = True 时适用。默认值为 0.0。

*massOffsetX*

一个 Double，指定圆柱截面中心相对于梁截面的局部 1 坐标。此参数仅在 *useFluidInertia* = True 时适用。默认值为 0.0。

*massOffsetY*

一个 Double，指定圆柱截面中心相对于梁截面的局部 2 坐标。此参数仅在 *useFluidInertia* = True 时适用。默认值为 0.0。

*material*

一个 odb_String，指定材料名称。当 *integration* 为 "DURING_ANALYSIS" 时需要材料。默认值为空字符串。

*table*

一个 odb_SequenceSequenceDouble，指定下述项目。默认值为空序列。

*outputPts*

一个 odb_SequenceSequenceDouble，指定请求输出的位置。默认值为空序列。

*centroid*

一个 odb_SequenceDouble，指定质心的 *X–Y* 坐标。默认值为 (0.0, 0.0)。

*shearCenter*

一个 odb_SequenceDouble，指定剪切中心的 *X–Y* 坐标。默认值为 (0.0, 0.0)。

**表数据**

表数据指定以下内容：
- E，截面的杨氏模量。
- G，截面的扭转剪切模量。
- 热膨胀系数（如果使用热膨胀）。
- 温度（如果数据依赖于温度）。
- 第一个场变量的值（如果数据依赖于场变量）。
- 第二个场变量的值。
- 等等。

**返回值**

一个 BeamSection 对象。

**异常**

无。

### 63.4.2 成员

BeamSection 对象具有与 [BeamSection](pt02ch63pyo04.md#ker-beamsection-beamsection-cpp) 方法参数相同名称和描述的成员。

此外，BeamSection 对象可以具有以下成员：

**原型**

```
odb_TransverseShearBeam beamTransverseShear() const;
```

*beamTransverseShear*

一个 [TransverseShearBeam](pt02ch63pyo24.md) 对象，指定横向剪切刚度属性。

### 63.4.3 对应的分析关键字

| [*BEAM GENERAL SECTION](../key/key-link.md#usb-kws-mbeamgensect) |
| --- |
| [*BEAM SECTION](../key/key-link.md#usb-kws-mbeamsection) |
| [*BEAM FLUID INERTIA](../key/key-link.md#usb-kws-mbeamfluidinertia) |
| [*CENTROID](../key/key-link.md#usb-kws-mcentroid) |
| [*DAMPING](../key/key-link.md#usb-kws-mdamping) |
| [*SHEAR CENTER](../key/key-link.md#usb-kws-mshearcenter) |
| [*SECTION POINTS](../key/key-link.md#usb-kws-msectionpoints) |
