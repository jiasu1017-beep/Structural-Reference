# 25.44 IncidentWave 对象

IncidentWave 对象为声学和耦合声学-结构分析定义入射波交互。

IncidentWave 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.44.1 IncidentWave(...)

此方法创建一个 IncidentWave 对象。

**路径**

```
mdb.models[*name*].IncidentWave
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 IncidentWave 对象的步骤名称。

*sourcePoint*

[Region](pt01ch45pyo03.md) 对象，指定入射波源点。

*standoffPoint*

[Region](pt01ch45pyo03.md) 对象，指定入射波 standoff 点。

当 *definition*=CONWEP 时，此参数无效。

*surface*

[Region](pt01ch45pyo03.md) 对象，指定定义入射波交互的表面。在涉及流体/表面边界的问题中，组成边界的流体表面和固体表面都必须指定入射波交互。

*interactionProperty*

字符串，指定与此交互关联的 [IncidentWaveProperty](pt01ch25pyo45.md) 对象。

**可选参数**

*definition*

 SymbolicConstant，指定要定义的入射波类型。该值对于线性扰动步骤必须为 PRESSURE。当值设置为 CONWEP 时需要 Explicit 步骤。可能的值为 PRESSURE、ACCELERATION、UNDEX 和 CONWEP。默认值为 PRESSURE。

*amplitude*

字符串，指定如果 *definition*=PRESSURE，则定义 standoff 点处流体压力时间历史的 [Amplitude](pt01ch03pyo01.md) 对象的名称。如果 *definition*=ACCELERATION，则此字符串指定定义 standoff 点处流体粒子加速度时间历史的 [Amplitude](pt01ch03pyo01.md) 对象的名称。此成员仅在 *definition*=PRESSURE 或 ACCELERATION 时可以指定。默认值为空字符串。

*imaginaryAmplitude*

字符串，指定定义 standoff 点处流体压力时间历史的虚部的 [Amplitude](pt01ch03pyo01.md) 对象的名称。此成员仅适用于线性扰动步骤，且仅在 *definition*=PRESSURE 时适用。默认值为空字符串。

*surfaceNormal*

三个浮点数组成的序列，指定流体表面法线的方向余弦的 X、Y 和 Z 分量。

此参数仅在 *definition*=UNDEX 时有效。

*initialDepth*

 `None` 或浮点数，指定 UNDEX 气泡的初始深度。默认值为 `None`。

此参数仅在 *definition*=UNDEX 时有效。

*referenceMagnitude*

浮点数，指定参考量级。

当 *definition*=CONWEP 时，此参数无效。

*detonationTime*

浮点数，指定引爆时间，以总时间给出。

此参数仅在 *definition*=CONWEP 时有效。

*magnitudeFactor*

浮点数，指定量级比例因子。默认值为 1.0。

此参数仅在 *definition*=CONWEP 时有效。

**返回值**

IncidentWave 对象。

**异常**

无。

### 25.44.2 setValues(...)

此方法修改 IncidentWave 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [IncidentWave](pt01ch25pyo44.md#ker-incidentwave-incidentwave-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.44.3 成员

IncidentWave 对象的成员与 [IncidentWave](pt01ch25pyo44.md#ker-incidentwave-incidentwave-pyc) 方法的参数具有相同的名称和描述。

### 25.44.4 对应的分析关键字

| [*INCIDENT WAVE INTERACTION](../key/key-link.md#usb-kws-hincidentwaveinteraction) |
| --- |



