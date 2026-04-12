# 9.30 FluidInletOutletBCState 对象

FluidInletOutletBCState 对象存储步骤中流体入口/出口边界条件的传播数据。该对象由 [FluidInletOutletBC](pt01ch09pyo29.md) 对象为每个步骤内部创建一个实例。该实例也由 [FluidInletOutletBC](pt01ch09pyo29.md) 对象内部删除。

FluidInletOutletBCState 对象没有构造函数或方法。

FluidInletOutletBCState 对象派生自 [BoundaryConditionState](pt01ch09pyo08.md) 对象。

**访问**

```
import load
mdb.models[*name*].steps[*name*].boundaryConditionStates[*name*]
```

### 9.30.1 成员

FluidInletOutletBCState 对象具有以下成员：

*momentumType*

SymbolicConstant，指定动量方程上定义的边界条件类型。可能的值为 NONE、PRESSURE 和 VELOCITY。默认值为 NONE。

*pressure*

`None` 或 Float，指定压力大小。默认值为 `None`。

*v1*

`None` 或 Float，指定全局坐标系 1 方向的速度分量。默认值为 `None`。

*v2*

`None` 或 Float，指定全局坐标系 2 方向的速度分量。默认值为 `None`。

*v3*

`None` 或 Float，指定全局坐标系 3 方向的速度分量。默认值为 `None`。

*momentumAmplitude*

`None` 或 String，指定动量方程上边界条件值随时间变化的幅值引用名称。默认值为 NONE。

*temperature*

`None` 或 Float，指定温度大小。默认值为 `None`。

*temperatureAmplitude*

`None` 或 String，指定温度随时间变化的幅值引用名称。默认值为 NONE。

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

*momentumTypeState*

SymbolicConstant，指定 *momentumType*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*pressureState*

SymbolicConstant，指定 *pressure*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*v1State*

SymbolicConstant，指定 *v1*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*v2State*

SymbolicConstant，指定 *v2*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*v3State*

SymbolicConstant，指定 *v3*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*momentumAmplitudeState*

SymbolicConstant，指定 *momentumAmplitude*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*temperatureState*

SymbolicConstant，指定 *temperature*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*temperatureAmplitudeState*

SymbolicConstant，指定 *temperatureAmplitude*成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

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
-