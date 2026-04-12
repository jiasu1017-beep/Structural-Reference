# 25.45 IncidentWaveProperty 对象

IncidentWaveProperty 对象是交互属性，定义由 [IncidentWave](pt01ch25pyo44.md) 对象引用的属性。

IncidentWaveProperty 对象派生自 [InteractionProperty](pt01ch25pyo48.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactionProperties[*name*]
```

### 25.45.1 IncidentWaveProperty(...)

此方法创建一个 IncidentWaveProperty 对象。

**路径**

```
mdb.models[*name*].IncidentWaveProperty
```

**必需参数**

*name*

字符串，指定交互属性存储库键。

**可选参数**

*definition*

 SymbolicConstant，指定要定义的波类型。可能的值为 PLANAR、SPHERICAL、DIFFUSE、AIR_BLAST 和 SURFACE_BLAST。默认值为 PLANAR。

*propagationModel*

 SymbolicConstant，指定球形传播模型。可能的值为 ACOUSTIC、UNDEX_CHARGE 和 GENERALIZED_DECAY。默认值为 ACOUSTIC。

此参数仅在 *definition*=SPHERICAL 时有效。

*soundSpeed*

浮点数，指定流体中的声速。

当 *definition*=AIR_BLAST 或 *definition*=SURFACE_BLAST 时，此参数无效。

*fluidDensity*

浮点数，指定流体质量密度。

当 *definition*=AIR_BLAST 或 *definition*=SURFACE_BLAST 时，此参数无效。

*specificHeatRatio*

 `None` 或浮点数，指定气体的比热比。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*gravity*

 `None` 或浮点数，指定重力加速度。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*atmosphericPressure*

 `None` 或浮点数，指定大气压力。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*dragCoefficient*

 `None` 或浮点数，指定流体阻力系数。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*dragExponent*

浮点数，指定流体阻力指数。默认值为 2.0。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*waveEffects*

布尔值，指定是否在流体和气体中包含波效应。默认值为 ON。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*chargeDensity*

 `None` 或浮点数，指定装药材料的密度。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*chargeMass*

 `None` 或浮点数，指定装药材料的质量。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*constantK1*

 `None` 或浮点数，指定装药材料常数 K。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*constantK2*

 `None` 或浮点数，指定装药材料常数 k。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*constantA*

 `None` 或浮点数，指定装药材料常数 A。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*constantB*

 `None` 或浮点数，指定装药材料常数 B。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*constantKc*

 `None` 或浮点数，指定装药材料常数 Kc。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*duration*

 `None` 或浮点数，指定气泡模拟的时间持续时间。默认值为 `None`。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*maximumSteps*

整数，指定气泡模拟的最大时间步数。默认值为 1500。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*relativeStepControl*

浮点数，指定相对步长控制参数。默认值为 110–11。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*absoluteStepControl*

浮点数，指定绝对步长控制参数。默认值为 110–11。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*stepControlExponent*

浮点数，指定步长控制指数。默认值为 0.2。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=UNDEX_CHARGE 时有效。

*genDecayA*

浮点数，指定与广义衰减传播模型关联的常数 A。默认值为 0.0。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=GENERALIZED_DECAY 时有效。

*genDecayB*

浮点数，指定与广义衰减传播模型关联的常数 B。默认值为 0.0。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=GENERALIZED_DECAY 时有效。

*genDecayC*

浮点数，指定与广义衰减传播模型关联的常数 C。默认值为 0.0。

此参数仅在 *definition*=SPHERICAL 且 *propagationModel*=GENERALIZED_DECAY 时有效。

*seedNumber*

整数，指定漫射源计算的种子数 (N)。N2 个源将用于模拟。

此参数仅在 *definition*=DIFFUSE 时有效。

*massTNT*

浮点数，指定 TNT 当量质量，以任何首选质量单位。

此参数仅在 *definition*=AIR_BLAST 或 *definition*=SURFACE_BLAST 时有效。

*massFactor*

浮点数，指定从首选质量单位转换为千克的乘法因子。默认值为 1.0。

此参数仅在 *definition*=AIR_BLAST 或 *definition*=SURFACE_BLAST 时有效。

*lengthFactor*

浮点数，指定从分析长度单位转换为米的乘法因子。默认值为 1.0。

此参数仅在 *definition*=AIR_BLAST 或 *definition*=SURFACE_BLAST 时有效。

*timeFactor*

浮点数，指定从分析时间单位转换为秒的乘法因子。默认值为 1.0。

此参数仅在 *definition*=AIR_BLAST 或 *definition*=SURFACE_BLAST 时有效。

*pressureFactor*

浮点数，指定从分析压力单位转换为帕斯卡的乘法因子。默认值为 1.0。

此参数仅在 *definition*=AIR_BLAST 或 *definition*=SURFACE_BLAST 时有效。

**返回值**

IncidentWaveProperty 对象。

**异常**

无。

### 25.45.2 setValues(...)

此方法修改 IncidentWaveProperty 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [IncidentWaveProperty](pt01ch25pyo45.md#ker-incidentwaveproperty-incidentwaveproperty-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 25.45.3 成员

IncidentWaveProperty 对象的成员与 [IncidentWaveProperty](pt01ch25pyo45.md#ker-incidentwaveproperty-incidentwaveproperty-pyc) 方法的参数具有相同的名称和描述。

### 25.45.4 对应的分析关键字

| [*INCIDENT WAVE INTERACTION PROPERTY](../key/key-link.md#usb-kws-mincidentwaveinteractionproperty) |
| --- |
| [*UNDEX CHARGE PROPERTY](../key/key-link.md#usb-kws-mundexchargeproperty) |
| [*CONWEP CHARGE PROPERTY](../key/key-link.md#usb-kws-mconwepchargeproperty) |



