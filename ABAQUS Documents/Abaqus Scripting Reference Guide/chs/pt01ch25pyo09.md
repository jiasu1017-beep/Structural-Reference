# 25.10 CavityRadiationState 对象

CavityRadiationState 对象存储 [CavityRadiation](pt01ch25pyo08.md) 对象的传播数据。CavityRadiation 对象会为每个步骤内部创建一个此对象的实例。该实例也会由 CavityRadiation 对象内部删除。

CavityRadiationState 对象没有构造函数或方法。

CavityRadiationState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.10.1 成员

CavityRadiationState 对象具有以下成员：

*blocking*

 SymbolicConstant，指定视角因子计算中要执行的阻挡检查。可能的值为 BLOCKING_ALL、NO_BLOCKING 和 PARTIAL_BLOCKING。

*blockingState*

 SymbolicConstant，指定 blocking 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*blockingSurfacesState*

 SymbolicConstant，指定 *blockingSurfaces* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*rangeOfView*

浮点数，指定超出此距离后不需要计算视角因子的距离，因为表面被认为彼此太远而无法"看见"（由于其他表面的阻挡）。

*rangeOfViewState*

 SymbolicConstant，指定 *rangeOfView* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*surfaceReflection*

布尔值，指定是否在腔体辐射计算中包含反射。默认值为 ON。

*surfaceReflectionState*

 SymbolicConstant，指定 *surfaceReflection* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*viewfactorAccuracyTol*

浮点数，指定视角因子计算的可接受容差。

*viewfactorAccuracyTolState*

 SymbolicConstant，指定 *viewfactorAccuracyTol* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*blockingSurfaces*

字符串元组，指定在腔体内部提供阻挡的表面。

*status*

 SymbolicConstant，指定 [InteractionState](pt01ch25pyo49.md) 对象的传播状态。可能的值为：
- NOT_YET_ACTIVE
- CREATED
- PROPAGATED
- MODIFIED
- DEACTIVATED
- NO_LONGER_ACTIVE
- TYPE_NOT_APPLICABLE
- INSTANCE_NOT_APPLICABLE
- BUILT_INTO_BASE_STATE

### 25.10.2 对应的分析关键字

| [*RADIATION VIEWFACTOR](#) |
| --- |



