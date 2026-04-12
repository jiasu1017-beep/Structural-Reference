# 29.34 DamageStabilizationCohesive 对象





DamageStabilizationCohesive 对象指定用于基于表面的相干行为或富集相干行为的损伤模型的粘性系数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].ductileDamageInitiation\
.damageStabilizationCohesive
...
import odbMaterial
session.odbs[*name*].materials[*name*].ductileDamageInitiation\
.damageStabilizationCohesive
...
```

### 29.34.1 DamageStabilizationCohesive(...)

此方法创建 DamageStabilizationCohesive 对象。

**路径**

```
mdb.models[*name*].materials[*name*].ductileDamageInitiation\
.DamageStabilizationCohesive
...
```

**必需参数**

无。

**可选参数**

*cohesiveCoeff*

`None` 或一个 Float，指定粘性系数。默认值为 `None`。

**返回值**

一个 DamageStabilizationCohesive 对象。

**异常**

RangeError。

### 29.34.2 setValues(...)

此方法修改 DamageStabilizationCohesive 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DamageStabilizationCohesive](pt01ch29pyo34.md#ker-damagestabilizationcohesive-damagestabilizationcohes-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.34.3 成员

DamageStabilizationCohesive 对象具有与 [DamageStabilizationCohesive](pt01ch29pyo34.md#ker-damagestabilizationcohesive-damagestabilizationcohes-pyc) 方法参数同名的成员，描述也相同。

### 29.34.4 对应的分析关键字

| [*DAMAGE STABILIZATION](../key/key-link.md#usb-kws-mdamagestabilization) |
| --- |




