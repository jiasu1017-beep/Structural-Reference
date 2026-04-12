# 9.25 EulerianMotionBC 对象

EulerianMotionBC 对象存储欧拉网格运动边界条件的数据。

EulerianMotionBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.25.1 EulerianMotionBC(...)

此方法创建 EulerianMotionBC 对象。

**路径**

```
mdb.models[*name*].EulerianMotionBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*instanceName*

String，指定欧拉部件实例的名称。

**可选参数**

*followRegion*

Boolean，指定网格是否跟随常规表面区域或欧拉表面。默认值为 ON。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*materialName*

String，指定要跟随的欧拉表面名称。此参数仅在 *followRegion*=False 时适用。

*ctrPosition1*

SymbolicConstant，指定欧拉网格中心在 1 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition1*

SymbolicConstant，指定网格在 1 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition1*

SymbolicConstant，指定网格在 1 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*expansionRatio1*

`None` 或 Float，指定 1 方向网格允许缩放的上限。如果 *expansionRatio1*=`None`，则没有上限。默认值为 `None`。

*contractRatio1*

Float，指定 1 方向网格允许缩放的下限。默认值为 0.0。

*ctrPosition2*

SymbolicConstant，指定欧拉网格中心在 2 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition2*

SymbolicConstant，指定网格在 2 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition2*

SymbolicConstant，指定网格在 2 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*expansionRatio2*

`None` 或 Float，指定 2 方向网格允许缩放的上限。如果 *expansionRatio2*=`None`，则没有上限。默认值为 `None`。

*contractRatio2*

Float，指定 2 方向网格允许缩放的下限。默认值为 0.0。

*ctrPosition3*

SymbolicConstant，指定欧拉网格中心在 3 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition3*

SymbolicConstant，指定网格在 3 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition3*

SymbolicConstant，指定网格在 3 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*expansionRatio3*

`None` 或 Float，指定 3 方向网格允许缩放的上限。如果 *expansionRatio3*=`None`，则没有上限。默认值为 `None`。

*contractRatio3*

Float，指定 3 方向网格允许缩放的下限。默认值为 0.0。

*allowContraction*

Boolean，指定网格是否允许收缩。默认值为 ON。

*aspectLimit*

Float，指定允许长宽比变化的最大值（三个网格长宽比中的任意一个：1-2、2-3、3-1）。默认值为 10.0。

*vmaxFactor*

Float，指定网格节点速度限制的乘数。默认值为 1.01。

*volThreshold*

Float，指定在确定将哪些节点包含在欧拉材料表面边界框计算中时的体积分数下限。此参数仅在 *followRegion*=False 时适用。默认值为 0.5。

*bufferSize*

`None` 或 Float，指定表面框和欧拉截面网格边界框之间的缓冲距离。默认值为 2.0。

**返回值**

EulerianMotionBC 对象。

**异常**

无。

### 9.25.2 setValues(...)

此方法修改创建该对象的步骤中现有 EulerianMotionBC 对象的数据。

**必需参数**

无。

**可选参数**

*instanceName*

String，指定欧拉部件实例的名称。

*followRegion*

Boolean，指定网格是否跟随常规表面区域或欧拉表面。默认值为 ON。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*materialName*

String，指定要跟随的欧拉表面名称。此参数仅在 *followRegion*=False 时适用。

*ctrPosition1*

SymbolicConstant，指定欧拉网格中心在 1 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition1*

SymbolicConstant，指定网格在 1 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition1*

SymbolicConstant，指定网格在 1 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*expansionRatio1*

`None` 或 Float，指定 1 方向网格允许缩放的上限。如果 *expansionRatio1*=`None`，则没有上限。默认值为 `None`。

*contractRatio1*

Float，指定 1 方向网格允许缩放的下限。默认值为 0.0。

*ctrPosition2*

SymbolicConstant，指定欧拉网格中心在 2 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition2*

SymbolicConstant，指定网格在 2 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition2*

SymbolicConstant，指定网格在 2 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*expansionRatio2*

`None` 或 Float，指定 2 方向网格允许缩放的上限。如果 *expansionRatio2*=`None`，则没有上限。默认值为 `None`。

*contractRatio2*

Float，指定 2 方向网格允许缩放的下限。默认值为 0.0。

*ctrPosition3*

SymbolicConstant，指定欧拉网格中心在 3 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition3*

SymbolicConstant，指定网格在 3 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition3*

SymbolicConstant，指定网格在 3 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*expansionRatio3*

`None` 或 Float，指定 3 方向网格允许缩放的上限。如果 *expansionRatio3*=`None`，则没有上限。默认值为 `None`。

*contractRatio3*

Float，指定 3 方向网格允许缩放的下限。默认值为 0.0。

*allowContraction*

Boolean，指定网格是否允许收缩。默认值为 ON。

*aspectLimit*

Float，指定允许长宽比变化的最大值（三个网格长宽比中的任意一个：1-2、2-3、3-1）。默认值为 10.0。

*vmaxFactor*

Float，指定网格节点速度限制的乘数。默认值为 1.01。

*volThreshold*

Float，指定在确定将哪些节点包含在欧拉材料表面边界框计算中时的体积分数下限。此参数仅在 *followRegion*=False 时适用。默认值为 0.5。

*bufferSize*

`None` 或 Float，指定表面框和欧拉截面网格边界框之间的缓冲距离。默认值为 2.0。

**返回值**

无。

**异常**

无。

### 9.25.3 setValuesInStep(...)

此方法修改指定步骤中现有 EulerianMotionBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*ctrPosition1*

SymbolicConstant，指定欧拉网格中心在 1 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition1*

SymbolicConstant，指定网格在 1 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition1*

SymbolicConstant，指定网格在 1 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*expansionRatio1*

`None` 或 Float，指定 1 方向网格允许缩放的上限。如果 *expansionRatio1*=`None`，则没有上限。默认值为 `None`。

*contractRatio1*

Float，指定 1 方向网格允许缩放的下限。默认值为 0.0。

*ctrPosition2*

SymbolicConstant，指定欧拉网格中心在 2 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition2*

SymbolicConstant，指定网格在 2 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition2*

SymbolicConstant，指定网格在 2 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*expansionRatio2*

`None` 或 Float，指定 2 方向网格允许缩放的上限。如果 *expansionRatio2*=`None`，则没有上限。默认值为 `None`。

*contractRatio2*

Float，指定 2 方向网格允许缩放的下限。默认值为 0.0。

*ctrPosition3*

SymbolicConstant，指定欧拉网格中心在 3 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition3*

SymbolicConstant，指定网格在 3 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition3*

SymbolicConstant，指定网格在 3 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*expansionRatio3*

`None` 或 Float，指定 3 方向网格允许缩放的上限。如果 *expansionRatio3*=`None`，则没有上限。默认值为 `None`。

*contractRatio3*

Float，指定 3 方向网格允许缩放的下限。默认值为 0.0。

*allowContraction*

Boolean，指定网格是否允许收缩。默认值为 ON。

*aspectLimit*

Float，指定允许长宽比变化的最大值（三个网格长宽比中的任意一个：1-2、2-3、3-1）。默认值为 10.0。

*vmaxFactor*

Float，指定网格节点速度限制的乘数。默认值为 1.01。

*volThreshold*

Float，指定在确定将哪些节点包含在欧拉材料表面边界框计算中时的体积分数下限。此参数仅在 *followRegion*=False 时适用。默认值为 0.5。

*bufferSize*

`None` 或 Float，指定表面框和欧拉截面网格边界框之间的缓冲距离。默认值为 2.0。

**返回值**

无。

**异常**

无。

### 9.25.4 成员

EulerianMotionBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*followRegion*

Boolean，指定网格是否跟随常规表面区域或欧拉表面。默认值为 ON。

*ctrPosition1*

SymbolicConstant，指定欧拉网格中心在 1 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*ctrPosition2*

SymbolicConstant，指定欧拉网格中心在 2 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*ctrPosition3*

SymbolicConstant，指定欧拉网格中心在 3 方向的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition1*

SymbolicConstant，指定网格在 1 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition2*

SymbolicConstant，指定网格在 2 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*posPosition3*

SymbolicConstant，指定网格在 3 方向的正向（最大）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition1*

SymbolicConstant，指定网格在 1 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition2*

SymbolicConstant，指定网格在 2 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*negPosition3*

SymbolicConstant，指定网格在 3 方向的负向（最小）边界的平移约束。可能的值为 FREE 和 FIXED。默认值为 FREE。

*expansionRatio1*

`None` 或 Float，指定 1 方向网格允许缩放的上限。如果 *expansionRatio1*=`None`，则没有上限。默认值为 `None`。

*expansionRatio2*

`None` 或 Float，指定 2 方向网格允许缩放的上限。如果 *expansionRatio2*=`None`，则没有上限。默认值为 `None`。

*expansionRatio3*

`None` 或 Float，指定 3 方向网格允许缩放的上限。如果 *expansionRatio3*=`None`，则没有上限。默认值为 `None`。

*contractRatio1*

Float，指定 1 方向网格允许缩放的下限。默认值为 0.0。

*contractRatio2*

Float，指定 2 方向网格允许缩放的下限。默认值为 0.0。

*contractRatio3*

Float，指定 3 方向网格允许缩放的下限。默认值为 0.0。

*allowContraction*

Boolean，指定网格是否允许收缩。默认值为 ON。

*aspectLimit*

Float，指定允许长宽比变化的最大值（三个网格长宽比中的任意一个：1-2、2-3、3-1）。默认值为 10.0。

*vmaxFactor*

Float，指定网格节点速度限制的乘数。默认值为 1.01。

*volThreshold*

Float，指定在确定将哪些节点包含在欧拉材料表面边界框计算中时的体积分数下限。此参数仅在 *followRegion*=False 时适用。默认值为 0.5。

*bufferSize*

`None` 或 Float，指定表面框和欧拉截面网格边界框之间的缓冲距离。默认值为 2.0。

*instanceName*

String，指定欧拉部件实例的名称。

*materialName*

String，指定要跟随的欧拉表面名称。此参数仅在 *followRegion*=False 时适用。

*category*

SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
