# 25.28 ElasticFoundation 对象

ElasticFoundation 对象定义机械基础。

ElasticFoundation 对象派生自 [Interaction](pt01ch25pyo01.md) 对象。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.28.1 ElasticFoundation(...)

此方法创建一个 ElasticFoundation 对象。

**路径**

```
mdb.models[*name*].ElasticFoundation
```

**必需参数**

*name*

字符串，指定存储库键。

*createStepName*

字符串，指定创建 ElasticFoundation 对象的步骤名称。*createStepName* 必须设置为 'Initial'。

*surface*

[Region](pt01ch45pyo03.md) 对象，指定基础适用的表面。

*stiffness*

浮点数，指定每面积（或对于梁每长度）的基础刚度。

**可选参数**

无。

**返回值**

ElasticFoundation 对象。

**异常**

无。

### 25.28.2 setValues(...)

此方法修改创建 ElasticFoundation 对象的步骤中现有 ElasticFoundation 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [ElasticFoundation](pt01ch25pyo28.md#ker-elasticfoundation-elasticfoundation-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 25.28.3 setValuesInStep(...)

此方法修改指定步骤中现有 ElasticFoundation 对象的传播数据。

**必需参数**

*stepName*

字符串，指定修改交互的步骤名称。

**可选参数**

*stiffness*

浮点数，指定每面积（或对于梁每长度）的基础刚度。

**返回值**

无。

**异常**

无。

### 25.28.4 成员

ElasticFoundation 对象的成员与 [ElasticFoundation](pt01ch25pyo28.md#ker-elasticfoundation-elasticfoundation-pyc) 方法的参数具有相同的名称和描述。

### 25.28.5 对应的分析关键字

| [*FOUNDATION](../key/key-link.md#usb-kws-mfoundation) |
| --- |



