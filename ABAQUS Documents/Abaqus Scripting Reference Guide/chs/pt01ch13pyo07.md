# 13.8 RigidBody 对象

RigidBody 对象将指定区域上的所有自由度约束到其关联参考点的自由度。

RigidBody 对象派生自 [Constraint](pt01ch13pyo01.md) 对象。

**访问权限**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.8.1 RigidBody(...)

此方法创建一个 RigidBody 对象。

**路径**

```
mdb.models[*name*].RigidBody
```

**必需参数**

*name*

字符串，指定约束存储库键。

*refPointRegion*

[Region](pt01ch45pyo03.md) 对象，指定参考点。

**可选参数**

*bodyRegion*

`None` 或 [Region](pt01ch45pyo03.md) 对象，指定约束到参考点运动的单元。默认值为 `None`。

*tieRegion*

`None` 或 [Region](pt01ch45pyo03.md) 对象，指定绑定到参考点运动的节点。默认值为 `None`。

*pinRegion*

`None` 或 [Region](pt01ch45pyo03.md) 对象，指定固定到参考点运动的节点。默认值为 `None`。

*surfaceRegion*

`None` 或 [Region](pt01ch45pyo03.md) 对象，指定约束到参考点运动的分析曲面。默认值为 `None`。

*refPointAtCOM*

布尔值，指定分析产品是否应重新计算参考点位置到质心处。默认值为 OFF。

*isothermal*

布尔值，指定是否应约束温度自由度。默认值为 OFF。

**返回值**

RigidBody 对象。

**异常**

无。

### 13.8.2 setValues(...)

此方法修改 RigidBody 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [RigidBody](pt01ch13pyo08.md#ker-rigidbody-rigidbody-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无。

**异常**

无。

### 13.8.3 成员

RigidBody 对象的成员与 [RigidBody](pt01ch13pyo08.md#ker-rigidbody-rigidbody-pyc) 方法的参数具有相同的名称和描述。

此外，RigidBody 对象还有以下成员：

*suppressed*

布尔值，指定约束是否被抑制。默认值为 OFF。

### 13.8.4 对应的分析关键字

| [*RIGID BODY](../key/key-link.md#usb-kws-mrigidbody) |
| --- |

