# 9.32 FluidWallConditionBCState 对象

FluidWallConditionBCState 对象存储步骤中流体壁条件边界条件的传播数据。该对象由 [FluidWallConditionBC](pt01ch09pyo31.md) 对象为每个步骤内部创建一个实例。该实例也由 [FluidWallConditionBC](pt01ch09pyo31.md) 对象内部删除。

FluidWallConditionBCState 对象没有构造函数或方法。

FluidWallConditionBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.32.1 成员

FluidWallConditionBCState 对象具有以下成员：

*type*

SymbolicConstant，指定壁条件边界条件的类型。可能的值为 INFILTRATION、NO_SLIP 和 SHEAR。默认值为 NO_SLIP。

*v1*

`None` 或 Float，指定全局坐标系 1 方向的速度分量。默认值为 `None`。

*v2*

`None` 或 Float，指定全局坐标系 2 方向的速度分量。默认值为 `None`。

*v3*

`None` 或 Float，指定全局坐标系 3 方向的速度分量。默认值为 `None`。

*velocityAmplitude*

`None` 或 String，指定速度随时间变化的幅值引用名称。默认值为 NONE。

*thermalEnergyType*

SymbolicConstant，指定热能方程上定义的边界条件类型。可能的值为 HEAT_FLUX、NONE 和 TEMPERATURE。默认值为 NONE。

*temperature*

`None` 或 Float，指定温度大小。默认值为 `None`。

*heatFlux*

`None` 或 Float，指定热通量大小。默认值为 `None`。

*thermalEnergyAmplitude*

`None` 或 String，指定热能方程上边界条件值随时间变化的幅值引用名称。默认值为 NONE。

*kineticEnergy*

`None` 或 Float，指定动能大小。默认值为 `None`。

*kineticEnergyAmplitude*

`None` 或 String，指定动能随时间变化的幅值引用名称。默认值为 NONE。

*dissipationRate*

`None` 或 Float，指定耗散率大小。默认值为 `None`。

*dissipationRateAmplitude*

`None` 或 String，指定耗散率随时间变化的幅值引用名称。默认值为 NONE。

*eddyViscosity*

`None` 或 Float，指定涡流粘度大小。默认值为 `None`。

*eddyViscosityAmplitude*

`None` 或 String，指定涡流粘度随时间变化的幅值引用名称。默认值为 NONE。

*typeState*

SymbolicConstant，指定 *type*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*v1State*

SymbolicConstant，指定 *v1*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*v2State*

SymbolicConstant，指定 *v2*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*v3State*

SymbolicConstant，指定 *v3*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*velocityAmplitudeState*

SymbolicConstant，指定 *velocityAmplitude*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*thermalEnergyTypeState*

SymbolicConstant，指定 *thermalEnergyType*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*temperatureState*

SymbolicConstant，指定 *temperature*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*heatFluxState*

SymbolicConstant，指定 *heatFlux*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*thermalEnergyAmplitudeState*

SymbolicConstant，指定 *thermalEnergyAmplitude*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*kineticEnergyState*

SymbolicConstant，指定 *kineticEnergy*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*kineticEnergyAmplitudeState*

SymbolicConstant，指定 *kineticEnergyAmplitude*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*dissipationRateState*

SymbolicConstant，指定 *dissipationRate*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*dissipationRateAmplitudeState*

SymbolicConstant，指定 *dissipationRateAmplitude*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*eddyViscosityState*

SymbolicConstant，指定 *eddyViscosity*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*eddyViscosityAmplitudeState*

SymbolicConstant，指定 *eddyViscosityAmplitude*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

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

### 9.32.2 对应分析关键字

| [*DSLOAD](../key/key-link.md#usb-kws-hdsload)，TYPE=ACCELERATION（载荷类型标签：DIST、TEMP、TURBNU、VELX、VELY 或 VELZ）|
| --- |

| [*DSFLUX](../key/key-link.md#usb-kws-hdsflux)（载荷类型标签：S）|
| --- |
