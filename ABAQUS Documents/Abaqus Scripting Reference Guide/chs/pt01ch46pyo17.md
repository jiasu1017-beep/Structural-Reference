# 46.17 MPCSection 对象

MPCSection 对象定义多点约束截面的属性。

MPCSection 对象派生自 [Section](pt01ch46pyo01.md) 对象。

**访问**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.17.1 MPCSection(...)

此方法创建 MPCSection 对象。

**Path**

```
mdb.models[*name*].MPCSection
session.odbs[*name*].MPCSection
```

**必需参数**

*name*

String，指定存储库键。

*mpcType*

SymbolicConstant，指定截面的 MPC 类型。可选值为 BEAM_MPC、ELBOW_MPC、PIN_MPC、LINK_MPC、TIE_MPC 和 USER_DEFINED。

**可选参数**

*userMode*

SymbolicConstant，指定用户定义的 MPC 的模式。可选值为 DOF_MODE 和 NODE_MODE。默认值为 DOF_MODE。

*userMode* 参数仅在 *mpcType*=USER_DEFINED 时适用。

*userType*

Int，指定用于区分用户定义的 MPCSection 中不同约束类型的值。默认值为 0。

*userType* 参数仅在 *mpcType*=USER_DEFINED 时适用。

**返回值**

MPCSection 对象。

**异常**

RangeError 和 InvalidNameError。

### 46.17.2 成员

MPCSection 对象的成员与 [MPCSection](pt01ch46pyo17.md#ker-mpcsection-mpcsection-pyc) 方法的参数具有相同的名称和描述。

### 46.17.3 对应分析关键字

| [*MPC*](../key/key-link.md#usb-kws-mmpc) |
| --- |
