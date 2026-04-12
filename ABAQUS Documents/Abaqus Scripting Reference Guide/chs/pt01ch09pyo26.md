# 9.26 EulerianMotionBCState 对象

EulerianMotionBCState 对象存储步骤中欧拉网格运动边界条件的传播数据。该对象由 [EulerianMotionBC](pt01ch09pyo25.md) 对象为每个步骤内部创建一个实例。该实例也由 [EulerianMotionBC](pt01ch09pyo25.md) 对象内部删除。

EulerianMotionBCState 对象没有构造函数或方法。

EulerianMotionBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.26.1 成员

EulerianMotionBCState 对象具有以下成员：

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

*amplitudeState*

SymbolicConstant，指定幅值引用的传播状态。可能的值为 UNSET、SET、UNCHANGED、FREED 和 MODIFIED。

*status*

SymbolicConstant，指定 [BoundaryConditionState](pt01ch09pyo08.md) 对象的传播状态。可能的值为：
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- PROPAGATED_FROM_BASE_STATE
- MODIFIED_FROM_BASE_STATE
- DEACTIVATED_FROM_BASE_STATE
- BUILT_INTO_MODES

*amplitude*

String，指定幅值引用的名称。如果边界条件没有幅值引用，则 String 为空。

### 9.26.2 对应分析关键字

| [*EULERIAN MESH MOTION](../key/key-link.md#usb-kws-heulmeshmotion)|
| --- |
