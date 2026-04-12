# 10.5 ElasPlasIsoBehavior 对象

ElasPlasIsoBehavior 对象表示弹性各向同性行为类型。

**访问**

```
import calibration
mdb.models[*name*].calibrations[*name*].behaviors.elasPlasIsoBehavior
```

### 10.5.1 ElasPlasIsoBehavior(...)

此方法创建 ElasPlasIsoBehavior 对象。

**路径**

```
mdb.models[*name*].calibrations[*name*].behaviors.ElasPlasIsoBehavior
```

**必需参数**

*name*

String，指定新行为的名称。

*typeName*

String，指定新 Behavior 的类型。值可以为"ElasIsoBehavior"、"ElasPlasIsoBehavior"、"FeFpBehavior"或用户插件行为类型。对于此对象，该值为"ElasPlasIsoBehavior"。

**可选参数**

无。

**返回值**

ElasPlasIsoBehavior 对象。

**异常**

InvalidNameError。

### 10.5.2 setValues(...)

此方法修改现有 ElasPlasIsoBehavior 对象的数据。

**必需参数**

无。

**可选参数**

*yieldPoint*

材料屈服点的应力/应变值。

*ultimatePoint*

材料极限点的应力/应变值。

*plasticPoints*

材料曲线塑性部分的应力/应变值。

*PoissonsRatio*

泊松比。

*elasticModulus*

材料曲线弹性部分的杨氏模量。

*ds1Name*

第一个数据集的名称。

*ds2Name*

第二个数据集的名称。

*materialName*

材料名称。

*plasticPointsRange*

材料塑性点的范围。

*name*

行为名称。

**返回值**

无。

**异常**

无。

### 10.5.3 成员

ElasPlasIsoBehavior 对象的成员与 [ElasPlasIsoBehavior](pt01ch10pyo05.md#ker-elasplasisobehavior-elasplasisobe