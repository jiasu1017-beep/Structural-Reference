# 55.11 QuantityType 对象

QuantityType 对象用于存储与 [XYData](pt01ch55pyo01.md) 或 [AxisData](pt01ch55pyo05.md) 对象关联的数量类型的物理维度和标签属性。

从 odb 创建 [XYData](pt01ch55pyo01.md) 对象时，会自动创建 QuantityType 对象。

QuantityType 对象可以使用下面描述的方法创建。

**访问**

```
import visualization
session.charts[*name*].axes1[*i*].axisData.curves[*i*].data\
.axis1QuantityType
session.charts[*name*].axes1[*i*].axisData.curves[*i*].data\
.axis2QuantityType
session.charts[*name*].axes1[*i*].axisData.quantityType
session.charts[*name*].axes2[*i*].axisData.curves[*i*].data\
.axis1QuantityType
session.charts[*name*].axes2[*i*].axisData.curves[*i*].data\
.axis2QuantityType
session.charts[*name*].axes2[*i*].axisData.quantityType
session.charts[*name*].curves[*name*].data.axis1QuantityType
session.charts[*name*].curves[*name*].data.axis2QuantityType
session.curves[*name*].data.axis1QuantityType
session.curves[*name*].data.axis2QuantityType
session.defaultChartOptions.defaultAxis1Options.axisData.curves[*i*]\
.data.axis1QuantityType
session.defaultChartOptions.defaultAxis1Options.axisData.curves[*i*]\
.data.axis2QuantityType
session.defaultChartOptions.defaultAxis1Options.axisData.quantityType
session.defaultChartOptions.defaultAxis2Options.axisData.curves[*i*]\
.data.axis1QuantityType
session.defaultChartOptions.defaultAxis2Options.axisData.curves[*i*]\
.data.axis2QuantityType
session.defaultChartOptions.defaultAxis2Options.axisData.quantityType
import odbAccess
session.odbs[*name*].userData.axis1QuantityType
session.odbs[*name*].userData.axis2QuantityType
import visualization
import xyPlot
session.odbs[*name*].userData.xyDataObjects[*name*].axis1QuantityType
session.odbs[*name*].userData.xyDataObjects[*name*].axis2QuantityType
session.xyDataObjects[*name*].axis1QuantityType
session.xyDataObjects[*name*].axis2QuantityType
session.xyPlots[*name*].charts[*name*].axes1[*i*].axisData.curves[*i*].data\
.axis1QuantityType
session.xyPlots[*name*].charts[*name*].axes1[*i*].axisData.curves[*i*].data\
.axis2QuantityType
session.xyPlots[*name*].charts[*name*].axes1[*i*].axisData.quantityType
session.xyPlots[*name*].charts[*name*].axes2[*i*].axisData.curves[*i*].data\
.axis1QuantityType
session.xyPlots[*name*].charts[*name*].axes2[*i*].axisData.curves[*i*].data\
.axis2QuantityType
session.xyPlots[*name*].charts[*name*].axes2[*i*].axisData.quantityType
session.xyPlots[*name*].charts[*name*].curves[*name*].data.axis1QuantityType
session.xyPlots[*name*].charts[*name*].curves[*name*].data.axis2QuantityType
session.xyPlots[*name*].curves[*name*].data.axis1QuantityType
session.xyPlots[*name*].curves[*name*].data.axis2QuantityType
```

### 55.11.1 QuantityType(...)

此方法创建 QuantityType 对象。

**路径**

```
session.QuantityType
```

```
xyPlot.QuantityType
```

**必需参数**

*type*

一个 SymbolicConstant，指定轴的物理维度。可能的值为：
- NONE。
- ACCELERATION。
- ACOUSTIC_INTENSITY。
- ANGLE。
- ANGULAR_MOMENTUM。
- ARC_LENGTH。
- AREA。
- AREA_VELOCITY_SQUARED，指定"速度平方每面积"。
- BIMOMENT。
- CURVATURE。
- CORIOLIS_LOAD。
- DAMAGE。
- DAMAGE_CRITERION。
- DENSITY。
- DENSITY_ROTATIONAL_ACCELERATION，指定"密度 * 角加速度"。
- DISPLACEMENT。
- ECURRENT_AREA_TIME，指定"每面积时间积分电流"。
- ELECTRIC_CHARGE。
- ELECTRIC_CURRENT。
- ELECTRIC_CURRENT_AREA，指定"单位面积电流"。
- ELECTRIC_POTENTIAL。
- ENERGY。
- ENERGY_DENSITY。
- ENERGY_RELEASE_RATE。
- EPOTENTIAL_GRADIENT，指定"电势梯度"。
- FREQUENCY。
- FORCE。
- FORCE_VOLUME，指定"每体积力"。
- HEAT_FLUX。
- HEAT_FLUX_AREA，指定"每面积热通量"。
- HEAT_FLUX_RATE。
- HEAT_FLUX_VOLUME，指定"每体积热通量"。
- LENGTH。
- LINEAR_PRESSURE。
- LUMIN，指定"发光强度"。
- MASS。
- MASS_FLOW_AREA，指定"每面积质量流量"。
- MASS_FLOW_AREA_RATE，指定"每面积质量流量率"。
- MASS_FLOW_RATE。
- MODE_NUMBER。
- MOMENT。
- NUMBER。
- PATH。
- PHASE。
- POSITION。
- PRESSURE。
- PRESSURE_GRADIENT。
- RATE。
- ROTARY_INERTIA。
- ROTATIONAL_ACCELERATION。
- ROTATIONAL_VELOCITY。
- STATUS。
- STRAIN。
- STRAIN_RATE。
- STRESS。
- STRESS_INTENS_FACTOR，指定"应力强度因子"。
- SUBSTANCE，指定"物质量"。
- TEMPERATURE。
- THICKNESS。
- TIME。
- TIME_INCREMENT。
- TIME_HEAT_FLUX，指定"时间积分热通量"。
- TIME_HEAT_FLUX_AREA，指定"每面积时间积分热通量"。
- TIME_VOLUME，指定"时间积分体积"。
- TIME_VOLUME_FLUX，指定"每面积时间积分体积通量"。
- TWIST。
- VELOCITY。
- VELOCITY_SQUARED。
- VOLUME。
- VOLUME_FLUX。
- VOLUME_FLUX_AREA，指定"每面积体积通量"。
- VOLUME_FRACTION。

**可选参数**

*label*

一个 String，指定此数量类型的标签。

**返回值**

QuantityType 对象。

**异常**

无。

### 55.11.2 setValues(...)

此方法修改 QuantityType 对象。

**必需参数**

无。

**可选参数**

*type*

一个 SymbolicConstant，指定轴的物理维度。可能的值为：
- NONE。
- ACCELERATION。
- ACOUSTIC_INTENSITY。
- ANGLE。
- ANGULAR_MOMENTUM。
- ARC_LENGTH。
- AREA。
- AREA_VELOCITY_SQUARED，指定"速度平方每面积"。
- BIMOMENT。
- CURVATURE。
- CORIOLIS_LOAD。
- DAMAGE。
- DAMAGE_CRITERION。
- DENSITY。
- DENSITY_ROTATIONAL_ACCELERATION，指定"密度 * 角加速度"。
- DISPLACEMENT。
- ECURRENT_AREA_TIME，指定"每面积时间积分电流"。
- ELECTRIC_CHARGE。
- ELECTRIC_CURRENT。
- ELECTRIC_CURRENT_AREA，指定"单位面积电流"。
- ELECTRIC_POTENTIAL。
- ENERGY。
- ENERGY_DENSITY。
- ENERGY_RELEASE_RATE。
- EPOTENTIAL_GRADIENT，指定"电势梯度"。
- FREQUENCY。
- FORCE。
- FORCE_VOLUME，指定"每体积力"。
- HEAT_FLUX。
- HEAT_FLUX_AREA，指定"每面积热通量"。
- HEAT_FLUX_RATE。
- HEAT_FLUX_VOLUME，指定"每体积热通量"。
- LENGTH。
- LINEAR_PRESSURE。
- LUMIN，指定"发光强度"。
- MASS。
- MASS_FLOW_AREA，指定"每面积质量流量"。
- MASS_FLOW_AREA_RATE，指定"每面积质量流量率"。
- MASS_FLOW_RATE。
- MODE_NUMBER。
- MOMENT。
- NUMBER。
- PATH。
- PHASE。
- POSITION。
- PRESSURE。
- PRESSURE_GRADIENT。
- RATE。
- ROTARY_INERTIA。
- ROTATIONAL_ACCELERATION。
- ROTATIONAL_VELOCITY。
- STATUS。
- STRAIN。
- STRAIN_RATE。
- STRESS。
- STRESS_INTENS_FACTOR，指定"应力强度因子"。
- SUBSTANCE，指定"物质量"。
- TEMPERATURE。
- THICKNESS。
- TIME。
- TIME_INCREMENT。
- TIME_HEAT_FLUX，指定"时间积分热通量"。
- TIME_HEAT_FLUX_AREA，指定"每面积时间积分热通量"。
- TIME_VOLUME，指定"时间积分体积"。
- TIME_VOLUME_FLUX，指定"每面积时间积分体积通量"。
- TWIST。
- VELOCITY。
- VELOCITY_SQUARED。
- VOLUME。
- VOLUME_FLUX。
- VOLUME_FLUX_AREA，指定"每面积体积通量"。
- VOLUME_FRACTION。

*label*

一个 String，指定此数量类型的标签。

**返回值**

无。

**异常**

无。

### 55.11.3 成员

QuantityType 对象具有与 [setValues](pt01ch55pyo11.md#ker-quantitytype-setvalues-pyc) 方法的参数具有相同名称和描述的成员。
