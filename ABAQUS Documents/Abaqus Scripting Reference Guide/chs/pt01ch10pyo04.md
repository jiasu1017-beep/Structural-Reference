# 10.4 ElasIsoBehavior 对象

ElasIsoBehavior 对象表示弹性各向同性行为类型。

**访问**

```
import calibration
mdb.models[*name*].calibrations[*name*].behaviors.elasIsoBehavior
```

### 10.4.1 ElasIsoBehavior(...)

此方法创建 ElasIsoBehavior 对象。

**路径**

```
mdb.models[*name*].calibrations[*name*].behaviors.ElasIsoBehavior
```

**必需参数**

*name*

String，指定新行为的名称。

*typeName*

String，指定新 Behavior 的类型。值可以为"ElasIsoBehavior"、"ElasPlasIsoBehavior"、"FeFpBehavior"或用户插件行为类型。对于此对象，该值为"ElasIsoBehavior"。

**可选参数**

无。

**返回值**

ElasIsoBehavior 对象。

**异常**

InvalidNameError。

### 10.4.2 setValues(...)

此方法修改现有 ElasIsoBehavior 对象的数据。

**必需参数**

无。

**可选参数**

*E*

杨氏模量。

*nu*

泊松比。

*ds1Name*

第一个数据集的名称。

*ds2Name*

第二个数据集的名称。

*materialName*

材料名称。

**返回值**

无。

**异常**

无。

### 10.4.3 成员

ElasIsoBehavior 对象的成员与 [ElasIsoBehavior](pt01ch10pyo04.md#ker-elasisobehavior-elasisobehavior-pyc) 方法的参数具有相同的名称和描述。
