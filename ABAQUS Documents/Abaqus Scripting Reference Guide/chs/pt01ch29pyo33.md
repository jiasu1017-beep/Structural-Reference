# 29.33 DamageStabilization 对象





DamageStabilization 对象指定纤维增强材料损伤模型的粘性系数。

**访问**

```
import material
mdb.models[*name*].materials[*name*].ductileDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].fldDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].flsdDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].hashinDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].johnsonCookDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].maxeDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].maxpeDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].maxpsDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].maxsDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].mkDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].msfldDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].quadeDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].quadsDamageInitiation\
.damageStabilization
mdb.models[*name*].materials[*name*].shearDamageInitiation\
.damageStabilization
import odbMaterial
session.odbs[*name*].materials[*name*].ductileDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].fldDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].flsdDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].hashinDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].johnsonCookDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].maxeDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].maxpeDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].maxpsDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].maxsDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].mkDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].msfldDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].quadeDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].quadsDamageInitiation\
.damageStabilization
session.odbs[*name*].materials[*name*].shearDamageInitiation\
.damageStabilization
```

### 29.33.1 DamageStabilization(...)

此方法创建 DamageStabilization 对象。

**路径**

```
mdb.models[*name*].materials[*name*].ductileDamageInitiation\
.DamageStabilization
...
```

**必需参数**

*fiberTensileCoeff*

一个 Float，指定纤维拉伸失效模式的粘性系数。

*fiberCompressiveCoeff*

一个 Float，指定纤维压缩失效模式的粘性系数。

*matrixTensileCoeff*

一个 Float，指定基体拉伸失效模式的粘性系数。

*matrixCompressiveCoeff*

一个 Float，指定基体压缩失效模式的粘性系数。

**可选参数**

无。

**返回值**

一个 DamageStabilization 对象。

**异常**

RangeError。

### 29.33.2 setValues(...)

此方法修改 DamageStabilization 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [DamageStabilization](pt01ch29pyo33.md#ker-damagestabilization-damagestabilization-pyc) 方法的参数相同。

**返回值**

无

**异常**

RangeError。

### 29.33.3 成员

DamageStabilization 对象具有与 [DamageStabilization](pt01ch29pyo33.md#ker-damagestabilization-damagestabilization-pyc) 方法参数同名的成员，描述也相同。

### 29.33.4 对应的分析关键字

| [*DAMAGE STABILIZATION](../key/key-link.md#usb-kws-mdamagestabilization) |
| --- |




