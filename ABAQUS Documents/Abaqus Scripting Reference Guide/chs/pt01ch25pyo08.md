# 25.8 CavityRadiation 对象

CavityRadiation 对象定义用于热辐射热传递的腔体，并控制视角因子的计算。

CavityRadiation 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.8.1 CavityRadiation(...)

此方法创建一个 CavityRadiation 对象。

**路径**

```
mdb.models[*name*].CavityRadiation
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建腔体辐射交互的步骤名称。

*surfaces*

[RegionArray](pt01ch45pyo03.md) 对象，指定要控制辐射视角因子的表面。

**可选参数**

*surfaceEmissivities*

字符串序列，指定包含表面发射率数据的腔体辐射属性的名称。每个指定表面一个名称。当 *surfaceReflection*=OFF 时，发射率数据将被忽略。

*ambientTemp*

 `None` 或浮点数，指定参考环境温度值，![](../graphics/ker_eqn00061.gif)。指定值表示开放腔体。默认值为 `None`。

*blocking*

 SymbolicConstant，指定视角因子计算中要执行的阻挡检查。可能的值为 BLOCKING_ALL、NO_BLOCKING 和 PARTIAL_BLOCKING。默认值为 BLOCKING_ALL。

*blockingSurfaces*

[RegionArray](pt01ch45pyo03.md) 对象，指定在腔体内部提供阻挡的表面。此参数仅在 *blocking*=PARTIAL_BLOCKING 时适用。

*rangeOfView*

 `None` 或浮点数，指定计算视角因子的表面面元之间的最大距离。更远的面元被认为距离太远，无法通过辐射效应交换大量热量，这些面元之间的视角因子假定为零。如果 *rangeOfView*=`None`，则没有上限。默认值为 `None`。

*surfaceReflection*

布尔值，指定是否在腔体辐射计算中包含热反射。默认值为 ON。

*viewfactorAccurTol*

浮点数，指定视角因子计算的可接受容差。默认值为 0.05。

*minInfinitesimalRatio*

浮点数，指定在视角因子计算中，当面元面积比高于此值时使用无穷小面积到有限面积的近似。默认值为 64.0。

*numPointsPerEdge*

整数，指定在视角因子计算的轮廓积分数值积分中，沿每条边使用的 Gauss 积分点数量。允许 1 到 5 个积分点。默认值为 3。

*minLumpedAreaDS*

浮点数，指定在视角因子计算中使用集总面积近似的无量纲距离平方值之上的值。默认值为 5.0。

*cyclicSymmetry*

布尔值，指定是否应用循环对称。此参数不能用于轴对称模型。默认值为 OFF。

*cyclicImages*

整数，指定构成由此对称形成的腔体的循环相似图像的数量。此参数仅在 *cyclicSymmetry*=ON 时适用。默认值为 2。

*cyclicRotPt*

[ModelDot](pt01ch07pyo12.md) 对象，指定旋转轴点。此参数仅在 *cyclicSymmetry*=ON 时适用。

*cyclicRotEndPt*

[ModelDot](pt01ch07pyo12.md) 对象，指定旋转轴端点。此参数仅适用于三维模型，且仅在 *cyclicSymmetry*=ON 时适用。

*cyclicSymPt*

[ModelDot](pt01ch07pyo12.md) 对象，指定对称轴端点。此参数仅在 *cyclicSymmetry*=ON 时适用。

*periodicSymmetries*

整数，指定要应用的周期对称数量。默认值为 0。

*periodicImages_1*

整数，指定用于计算由第一个周期对称引起的腔体视角因子的重复次数。结果是腔体由模型中定义的腔体表面加上两倍的 *periodicImages_1* 值组成。此参数仅在 *periodicSymmetries* 大于零时适用。默认值为 2。

*periodicImages_2*

整数，指定用于计算由第二个周期对称引起的腔体视角因子的重复次数。结果是腔体由模型中定义的腔体表面加上两倍的 *periodicImages_2* 值组成。此参数仅在 *periodicSymmetries* 大于一时适用。默认值为 2。

*periodicImages_3*

整数，指定用于计算由第三个周期对称引起的腔体视角因子的重复次数。结果是腔体由模型中定义的腔体表面加上两倍的 *periodicImages_3* 值组成。此参数仅在 *periodicSymmetries* = 3 时适用。默认值为 2。

*periodicSymAxis_1*

直边、[Datum](pt01ch15pyo01.md) 对象表示基准轴，或 ElementEdge 对象，指示二维模型中的第一条对称线。此参数仅适用于二维模型，且当 *periodicSymmetries* 大于零时适用。

*periodicSymAxis_2*

直边、[Datum](pt01ch15pyo01.md) 对象表示基准轴，或 ElementEdge 对象，指示二维模型中的第二条对称线。此参数仅适用于二维模型，且当 *periodicSymmetries* = 2 时适用。

*periodicSymPlane_1*

平面面、ElementFace 或 [Datum](pt01ch15pyo01.md) 对象表示基准平面；指示三维模型中的第一个对称平面。此参数仅适用于三维模型，且当 *periodicSymmetries* 大于零时适用。

*periodicSymPlane_2*

平面面、ElementFace 或 [Datum](pt01ch15pyo01.md) 对象表示基准平面；指示三维模型中的第二个对称平面。此参数仅适用于三维模型，且当 *periodicSymmetries* 大于一时适用。

*periodicSymPlane_3*

平面面、ElementFace 或 [Datum](pt01ch15pyo01.md) 对象表示基准平面；指示三维模型中的第三个对称平面。此参数仅适用于三维模型，且当 *periodicSymmetries* = 3 时适用。

*periodicDistance_1*

浮点数序列的序列，指定描述第一个周期对称的周期距离的向量两点。每个点由三个坐标的元组定义其位置。此参数仅在 *periodicSymmetries* 大于零时适用。默认值为空序列。

*periodicDistance_2*

浮点数序列的序列，指定描述第二个周期对称的周期距离的向量两点。每个点由三个坐标的元组定义其位置。此参数仅在 *periodicSymmetries* 大于一时适用。默认值为空序列。

*periodicDistance_3*

浮点数序列的序列，指定描述第三个周期对称的周期距离的向量两点。每个点由三个坐标的元组定义其位置。此参数仅在 *periodicSymmetries* = 3 时适用。默认值为空序列。

*periodicSymZ*

 `None` 或浮点数，指定轴对称模型中表示对称参考线的 Z 值。此参数仅适用于轴对称模型，且当 *periodicSymmetries* = 1 时适用。默认值为 `None`。

*periodicDistZ*

 `None` 或浮点数，指定轴对称模型中表示周期距离的 Z 值。此参数仅适用于轴对称模型，且当 *periodicSymmetries* = 1 时适用。默认值为 `None`。

*reflectionSymmetries*

整数，指定要应用的反射对称数量。默认值为 0。

*reflectionSymAxis_1*

直边、[Datum](pt01ch15pyo01.md) 对象表示基准轴，或 ElementEdge 对象，指示二维模型中的第一条对称线。此参数仅适用于二维模型，且当 *reflectionSymmetries* 大于零时适用。

*reflectionSymAxis_2*

直边、[Datum](pt01ch15pyo01.md) 对象表示基准轴，或 ElementEdge 对象，指示二维模型中的第二条对称线。此参数仅适用于二维模型，且当 *reflectionSymmetries* = 2 时适用。

*reflectionSymPlane_1*

平面面、ElementFace 或 [Datum](pt01ch15pyo01.md) 对象表示基准平面；指示三维模型中的第一个对称平面。此参数仅适用于三维模型，且当 *reflectionSymmetries* 大于零时适用。

*reflectionSymPlane_2*

平面面、ElementFace 或 [Datum](pt01ch15pyo01.md) 对象表示基准平面；指示三维模型中的第二个对称平面。此参数仅适用于三维模型，且当 *reflectionSymmetries* 大于一时适用。

*reflectionSymPlane_3*

平面面、ElementFace 或 [Datum](pt01ch15pyo01.md) 对象表示基准平面；指示三维模型中的第三个对称平面。此参数仅适用于三维模型，且当 *reflectionSymmetries* = 3 时适用。

*reflectionSymZ*

 `None` 或浮点数，指定轴对称模型中表示对称参考线的 Z 值。此参数仅适用于轴对称模型，且当 *reflectionSymmetries* = 1 时适用。默认值为 `None`。

**返回值**

CavityRadiation 对象。

**异常**

无。

### 25.8.2 setValues(...)

此方法修改创建 CavityRadiation 对象的步骤中现有 CavityRadiation 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [CavityRadiation](pt01ch25pyo08.md#ker-cavityradiation-cavityradiation-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.8.3 setValuesInStep(...)

此方法修改指定步骤中现有 CavityRadiation 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

*blocking*

 SymbolicConstant，指定视角因子计算中要执行的阻挡检查。可能的值为 BLOCKING_ALL、NO_BLOCKING 和 PARTIAL_BLOCKING。默认值为 BLOCKING_ALL。

*blockingSurfaces*

[RegionArray](pt01ch45pyo03.md) 对象，指定在腔体内部提供阻挡的表面。此参数仅在 *blocking*=PARTIAL_BLOCKING 时适用。

*rangeOfView*

 `None` 或浮点数，指定计算视角因子的表面面元之间的最大距离。更远的面元被认为距离太远，无法通过辐射效应交换大量热量，这些面元之间的视角因子假定为零。如果 *rangeOfView*=`None`，则没有上限。默认值为 `None`。

*surfaceReflection*

布尔值，指定是否在腔体辐射计算中包含热反射。默认值为 ON。

*viewfactorAccurTol*

浮点数，指定视角因子计算的可接受容差。默认值为 0.05。

**返回值**

无。

**异常**

无。

### 25.8.4 成员

CavityRadiation 对象可以具有以下成员：

*name*

字符串，指定存储库键。

*ambientTemp*

 `None` 或浮点数，指定参考环境温度值，![](../graphics/ker_eqn00061.gif)。指定值表示开放腔体。默认值为 `None`。

*blocking*

 SymbolicConstant，指定视角因子计算中要执行的阻挡检查。可能的值为 BLOCKING_ALL、NO_BLOCKING 和 PARTIAL_BLOCKING。默认值为 BLOCKING_ALL。

*rangeOfView*

 `None` 或浮点数，指定计算视角因子的表面面元之间的最大距离。更远的面元被认为距离太远，无法通过辐射效应交换大量热量，这些面元之间的视角因子假定为零。如果 *rangeOfView*=`None`，则没有上限。默认值为 `None`。

*surfaceReflection*

布尔值，指定是否在腔体辐射计算中包含热反射。默认值为 ON。

*viewfactorAccurTol*

浮点数，指定视角因子计算的可接受容差。默认值为 0.05。

*minInfinitesimalRatio*

浮点数，指定在视角因子计算中，当面元面积比高于此值时使用无穷小面积到有限面积的近似。默认值为 64.0。

*numPointsPerEdge*

整数，指定在视角因子计算的轮廓积分数值积分中，沿每条边使用的 Gauss 积分点数量。允许 1 到 5 个积分点。默认值为 3。

*minLumpedAreaDS*

浮点数，指定在视角因子计算中使用集总面积近似的无量纲距离平方值之上的值。默认值为 5.0。

*cyclicSymmetry*

布尔值，指定是否应用循环对称。此参数不能用于轴对称模型。默认值为 OFF。

*cyclicImages*

整数，指定构成由此对称形成的腔体的循环相似图像的数量。此参数仅在 *cyclicSymmetry*=ON 时适用。默认值为 2。

*periodicSymmetries*

整数，指定要应用的周期对称数量。默认值为 0。

*periodicImages_1*

整数，指定用于计算由第一个周期对称引起的腔体视角因子的重复次数。结果是腔体由模型中定义的腔体表面加上两倍的 *periodicImages_1* 值组成。此参数仅在 *periodicSymmetries* 大于零时适用。默认值为 2。

*periodicImages_2*

整数，指定用于计算由第二个周期对称引起的腔体视角因子的重复次数。结果是腔体由模型中定义的腔体表面加上两倍的 *periodicImages_2* 值组成。此参数仅在 *periodicSymmetries* 大于一时适用。默认值为 2。

*periodicImages_3*

整数，指定用于计算由第三个周期对称引起的腔体视角因子的重复次数。结果是腔体由模型中定义的腔体表面加上两倍的 *periodicImages_3* 值组成。此参数仅在 *periodicSymmetries* = 3 时适用。默认值为 2。

*periodicSymZ*

 `None` 或浮点数，指定轴对称模型中表示对称参考线的 Z 值。此参数仅适用于轴对称模型，且当 *periodicSymmetries* = 1 时适用。默认值为 `None`。

*periodicDistZ*

 `None` 或浮点数，指定轴对称模型中表示周期距离的 Z 值。此参数仅适用于轴对称模型，且当 *periodicSymmetries* = 1 时适用。默认值为 `None`。

*reflectionSymmetries*

整数，指定要应用的反射对称数量。默认值为 0。

*reflectionSymZ*

 `None` 或浮点数，指定轴对称模型中表示对称参考线的 Z 值。此参数仅适用于轴对称模型，且当 *reflectionSymmetries* = 1 时适用。默认值为 `None`。

*createStepName*

字符串，指定创建腔体辐射交互的步骤名称。

*surfaces*

[RegionArray](pt01ch45pyo03.md) 对象，指定要控制辐射视角因子的表面。

*surfaceEmissivities*

字符串元组，指定包含表面发射率数据的腔体辐射属性的名称。每个指定表面一个名称。当 *surfaceReflection*=OFF 时，发射率数据将被忽略。

*blockingSurfaces*

[RegionArray](pt01ch45pyo03.md) 对象，指定在腔体内部提供阻挡的表面。此参数仅在 *blocking*=PARTIAL_BLOCKING 时适用。

*cyclicRotPt*

[ModelDot](pt01ch07pyo12.md) 对象，指定旋转轴点。此参数仅在 *cyclicSymmetry*=ON 时适用。

*cyclicRotEndPt*

[ModelDot](pt01ch07pyo12.md) 对象，指定旋转轴端点。此参数仅适用于三维模型，且仅在 *cyclicSymmetry*=ON 时适用。

*cyclicSymPt*

[ModelDot](pt01ch07pyo12.md) 对象，指定对称轴端点。此参数仅在 *cyclicSymmetry*=ON 时适用。

*periodicDistance_1*

浮点数元组的元组，指定描述第一个周期对称的周期距离的向量两点。每个点由三个坐标的元组定义其位置。此参数仅在 *periodicSymmetries* 大于零时适用。默认值为空序列。

*periodicDistance_2*

浮点数元组的元组，指定描述第二个周期对称的周期距离的向量两点。每个点由三个坐标的元组定义其位置。此参数仅在 *periodicSymmetries* 大于一时适用。默认值为空序列。

*periodicDistance_3*

浮点数元组的元组，指定描述第三个周期对称的周期距离的向量两点。每个点由三个坐标的元组定义其位置。此参数仅在 *periodicSymmetries* = 3 时适用。默认值为空序列。

### 25.8.5 对应的分析关键字

| [*CAVITY DEFINITION](../key/key-link.md#usb-kws-mcavitydef), SET PROPERTY |
| --- |
| [*CYCLIC](../key/key-link.md#usb-kws-hcyclicsym) |
| [*EMISSIVITY](../key/key-link.md#usb-kws-memissivity) |
| [*PERIODIC](../key/key-link.md#usb-kws-hperiodicsym) |
| [*RADIATION SYMMETRY](../key/key-link.md#usb-kws-hradsymmetry) |
| [*RADIATION VIEWFACTOR](#) |
| [*REFLECTION](../key/key-link.md#usb-kws-hreflectionsym) |



