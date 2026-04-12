# 10.6 FeFpBehavior 对象

FeFpBehavior 对象表示具有永久集行为的超弹性类型。

**访问**

```
import calibration
mdb.models[*name*].calibrations[*name*].behaviors.feFpBehavior
```

### 10.6.1 FeFpBehavior(...)

此方法创建 FeFpBehavior 对象。

**路径**

```
mdb.models[*name*].calibrations[*name*].behaviors.FeFpBehavior
```

**必需参数**

*name*

String，指定新行为的名称。

*typeName*

String，指定新 Behavior 的类型。值可以为"ElasIsoBehavior"、"ElasPlasIsoBehavior"、"FeFpBehavior"或用户插件行为类型。对于此对象，该值为"FeFpBehavior"。

**可选参数**

无。

**返回值**

FeFpBehavior 对象。

**异常**

InvalidNameError。

### 10.6.2 setValues(...)

此方法修改现有 FeFpBehavior 对象的数据。

**必需参数**

无。

**可选参数**

*uniaxialName*

单轴数据集的名称。

*biaxialName*

双轴数据集的名称。

*interpolation*

'linear' 指定数据点之间的线性插值，否则为 'logarithmic'（对数）。

*uniWeight*

单轴权重因子，uniWeight + biWeight 应该等于 1.0。

*biWeight*

双轴权重因子，uniWeight + biWeight 应该等于 1.0。

**返回值**

无。

**异常**

无。

### 10.6.3 成员

FeFpBehavior 对象的成员与 [FeFpBehavior](pt01ch10pyo06.md#ker-fefpbehavior-fefpbehavior-pyc) 方法的参数具有相同的名称和描述。
