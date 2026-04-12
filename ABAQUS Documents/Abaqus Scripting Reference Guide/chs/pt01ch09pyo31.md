# 9.31 FluidWallConditionBC 对象

FluidWallConditionBC 对象存储流体壁条件边界条件的数据。

FluidWallConditionBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.31.1 FluidWallConditionBC(...)

此方法创建 FluidWallConditionBC 对象。

**路径**

```
mdb.models[*name*].FluidWallConditionBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*fieldName*

String，指定与此边界条件关联的 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称。*fieldName* 参数仅在 *distributionType*=FIELD 或 *distributionType*=DISCRETE_FIELD 时适用。默认值为空字符串。

*distributionType*

SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM、USER_DEFINED、FIELD 和 DISCRETE_FIELD。默认值为 UNIFORM。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

*type*

SymbolicConstant，指定流体壁条件边界条件的类型。可能的值为 INFILTRATION、NO_SLIP 和 SHEAR。默认值为 NO_SLIP。

*v1*

Float 或 SymbolicConstant UNSET，指定全局坐标系 1 方向的速度分量。默认值为 UNSET。

*v2*

Float 或 SymbolicConstant UNSET，指定全局坐标系 2 方向的速度分量。默认值为 UNSET。

*v3*

Float 或 SymbolicConstant UNSET，指定全局坐标系 3 方向的速度分量。默认值为 UNSET。

*velocityAmplitude*

String 或 SymbolicConstant UNSET，指定速度随时间变化的幅值引用名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。

*thermalEnergyType*

SymbolicConstant，指定热能方程上定义的边界条件类型。可能的值为 HEAT_FLUX、TEMPERATURE 和 UNSET。默认值为 UNSET。

*temperature*

Float 或 SymbolicConstant UNSET，指定温度大小。当 *thermalEnergyType*=TEMPERATURE 时使用数值。默认值为 UNSET。

*heatFlux*

Float 或 SymbolicConstant UNSET，指定热通量大小。当 *thermalEnergyType*=HEAT_FLUX 时使用数值。默认值为 UNSET。

*thermalEnergyAmplitude*

String 或 SymbolicConstant UNSET，指定热能方程上边界条件值随时间变化的幅值引用名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。

*kineticEnergy*

Float 或 SymbolicConstant UNSET，指定动能大小。默认值为 UNSET。

*kineticEnergyAmplitude*

String 或 SymbolicConstant UNSET，指定动能随时间变化的幅值引用名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。

*dissipationRate*

Float 或 SymbolicConstant UNSET，指定耗散率大小。默认值为 UNSET。

*dissipationRateAmplitude*

String 或 SymbolicConstant UNSET，指定耗散率随时间变化的幅值引用名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。

*eddyViscosity*

Float 或 SymbolicConstant UNSET，指定涡流粘度大小。默认值为 UNSET。

*eddyViscosityAmplitude*

String 或 SymbolicConstant UNSET，指定涡流粘度随时间变化的幅值引用名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。

**返回值**

FluidWallConditionBC 对象。

**异常**

无。

### 9.31.2 setValues(...)

此方法修改创建该对象的步骤中现有 FluidWallConditionBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [FluidWallConditionBC](pt01ch09pyo31.md#ker-fluidwallconditionbc-fluidwallconditionbc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.31.3 setValuesInStep(...)

此方法修改指定步骤中现有 FluidWallConditionBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*type*

SymbolicConstant，指定流体壁条件边界条件的类型。可能的值为 INFILTRATION、NO_SLIP 和 SHEAR。

*v1*

Float 或 SymbolicConstant FREED，指定全局坐标系 1 方向的速度分量。使用 FREED 删除先前定义的值。

*v2*

Float 或 SymbolicConstant FREED，指定全局坐标系 2 方向的速度分量。使用 FREED 删除先前定义的值。

*v3*

Float 或 SymbolicConstant FREED，指定全局坐标系 3 方向的速度分量。使用 FREED 删除先前定义的值。

*velocityAmplitude*

String 或 SymbolicConstant FREED，指定速度随时间变化的幅值引用名称。如果边界条件没有幅值引用，应使用 FREED。

*thermalEnergyType*

SymbolicConstant，指定热能方程上定义的边界条件类型。可能的值为 FREED、HEAT_FLUX 和 TEMPERATURE。使用 FREED 删除先前定义的值。

*temperature*

Float 或 SymbolicConstant FREED，指定温度大小。当 *thermalEnergyType*=TEMPERATURE 时使用数值。否则，使用 FREED 删除先前定义的值。

*heatFlux*

Float 或 SymbolicConstant FREED，指定热通量大小。当 *thermalEnergyType*=HEAT_FLUX 时使用数值。否则，使用 FREED 删除先前定义的值。

*thermalEnergyAmplitude*

String 或 SymbolicConstant FREED，指定热能方程上边界条件值随时间变化的幅值引用名称。如果边界条件没有幅值引用，应使用 FREED。

*kineticEnergy*

Float 或 SymbolicConstant FREED，指定动能大小。使用 FREED 删除先前定义的值。

*kineticEnergyAmplitude*

String 或 SymbolicConstant FREED，指定动能随时间变化的幅值引用名称。如果边界条件没有幅值引用，应使用 FREED。

*dissipationRate*

Float 或 SymbolicConstant FREED，指定耗散率大小。使用 FREED 删除先前定义的值。

*dissipationRateAmplitude*

String 或 SymbolicConstant FREED，指定耗散率随时间变化的幅值引用名称。如果边界条件没有幅值引用，应使用 FREED。

*eddyViscosity*

Float 或 SymbolicConstant FREED，指定涡流粘度大小。使用 FREED 删除先前定义的值。

*eddyViscosityAmplitude*

String 或 SymbolicConstant FREED，指定涡流粘度随时间变化的幅值引用名称。如果边界条件没有幅值引用，应使用 FREED。

**返回值**

无。

**异常**

无。

### 9.31.4 成员

FluidWallConditionBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*distributionType*

SymbolicConstant，指定边界条件在空间上的分布方式。可能的值为 UNIFORM、USER_DEFINED、FIELD 和 DISCRETE_FIELD。默认值为 UNIFORM。

*fieldName*

String，指定与此边界条件关联的 [AnalyticalField](pt01ch21pyo02.md) 或 [DiscreteField](pt01ch21pyo04.md) 对象的名称。*fieldName* 参数仅在 *distributionType*=FIELD 或 *distributionType*=DISCRETE_FIELD 时适用。默认值为空字符串。

*category*

SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
