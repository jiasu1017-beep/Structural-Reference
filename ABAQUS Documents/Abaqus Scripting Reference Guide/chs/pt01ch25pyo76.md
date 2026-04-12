# 25.76 SurfaceToSurfaceExpState 对象

SurfaceToSurfaceExpState 对象在步骤中存储 [SurfaceToSurfaceContactExp](pt01ch25pyo74.md) 对象的传播数据。SurfaceToSurfaceContactExp 对象会为每个步骤内部创建一个此对象的实例。该实例也会由 SurfaceToSurfaceContactExp 对象内部删除。

SurfaceToSurfaceExpState 对象没有构造函数或方法。

SurfaceToSurfaceExpState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.76.1 成员

SurfaceToSurfaceExpState 对象具有以下成员：

*interactionPropertyState*

 SymbolicConstant，指定 *interactionProperty* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*contactControlsState*

 SymbolicConstant，指定 *contactControls* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*interactionProperty*

字符串，指定与此交互关联的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。

*contactControls*

字符串，指定与此交互关联的 [ContactControl](pt01ch25pyo16.md) 对象的名称。

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

### 25.76.2 对应的分析关键字

| [*CONTACT CONTROLS](../key/key-link.md#usb-kws-hcontactcontrols) |
| --- |
| [*CONTACT PAIR](../key/key-link.md#usb-kws-hcontactpair) |



