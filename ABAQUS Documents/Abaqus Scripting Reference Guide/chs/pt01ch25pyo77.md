# 25.77 SurfaceToSurfaceStdState 对象

SurfaceToSurfaceStdState 对象在步骤中存储 [SurfaceToSurfaceContactStd](pt01ch25pyo75.md) 对象的传播数据。SurfaceToSurfaceContactStd 对象会为每个步骤内部创建一个此对象的实例。该实例也会由 SurfaceToSurfaceContactStd 对象内部删除。

SurfaceToSurfaceStdState 对象没有构造函数或方法。

SurfaceToSurfaceStdState 对象派生自 [InteractionState](pt01ch25pyo49.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].steps[*name*].interactionStates[*name*]
```

### 25.77.1 成员

SurfaceToSurfaceStdState 对象具有以下成员：

*interactionPropertyState*

 SymbolicConstant，指定 *interactionProperty* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*interferenceType*

 SymbolicConstant，指定干扰类型。可能的值为 NONE、SHRINK_FIT 和 UNIFORM。

*interferenceTypeState*

 SymbolicConstant，指定 *interferenceType* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*overclosure*

浮点数，指定允许的过闭合。

*overclosureState*

 SymbolicConstant，指定 *overclosure* 成员的传播状态。可能的值为 COMPUTED 和 DIRECTION_COSINE。

*interferenceDirectionType*

 SymbolicConstant，指定干扰方向类型。可能的值为 COMPUTED 和 DIRECTION_COSINE。

*interferenceDirectionTypeState*

 SymbolicConstant，指定 *interferenceDirectionType* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*directionState*

 SymbolicConstant，指定 *direction* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*amplitudeState*

 SymbolicConstant，指定 *amplitude* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*contactControlsState*

 SymbolicConstant，指定 *contactControls* 成员的传播状态。可能的值为 UNSET、SET、UNCHANGED 和 FREED。

*interactionProperty*

字符串，指定与此交互关联的 [ContactProperty](pt01ch25pyo21.md) 对象的名称。

*amplitude*

字符串，指定定义步骤中规定干扰大小的 Amplitude 对象的名称。

*contactControls*

字符串，指定与此交互关联的 [ContactControl](pt01ch25pyo16.md) 对象的名称。

*direction*

三个浮点数组成的元组，指定以下内容：
- ![](../graphics/ker_eqn00083.gif)-干扰方向向量的方向余弦。
- ![](../graphics/ker_eqn00084.gif)-干扰方向向量的方向余弦。
- ![](../graphics/ker_eqn00085.gif)-干扰方向向量的方向余弦。

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

### 25.77.2 对应的分析关键字

| [*CONTACT CONTROLS](../key/key-link.md#usb-kws-hcontactcontrols) |
| --- |
| [*CONTACT PAIR](../key/key-link.md#usb-kws-hcontactpair) |
| [*CONTACT INTERFERENCE](../key/key-link.md#usb-kws-hcontactinterfer) |



