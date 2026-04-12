# 60.34 DamageStabilizationCohesive 对象

DamageStabilizationCohesive 对象为基于表面的内聚行为或富集内聚行为的损伤模型指定粘度系数。

**访问**

```
materialApi.materials()[*name*].ductileDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].fldDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].flsdDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].hashinDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].johnsonCookDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].maxeDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].maxpeDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].maxpsDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].maxsDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].mkDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].msfldDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].quadeDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].quadsDamageInitiation()\
.damageStabilizationCohesive()
materialApi.materials()[*name*].shearDamageInitiation()\
.damageStabilizationCohesive()
```

### 60.34.1 DamageStabilizationCohesive(...)

此方法创建一个 DamageStabilizationCohesive 对象。

**路径**

```
materialApi.materials()[*name*].ductileDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].fldDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].flsdDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].hashinDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].johnsonCookDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].maxeDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].maxpeDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].maxpsDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].maxsDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].mkDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].msfldDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].quadeDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].quadsDamageInitiation()\
.DamageStabilizationCohesive
materialApi.materials()[*name*].shearDamageInitiation()\
.DamageStabilizationCohesive
```

**原型**

```
odb_DamageStabilizationCohesive&
DamageStabilizationCohesive(odb_Union cohesiveCoeff);
```

**必需参数**

无。

**可选参数**

*cohesiveCoeff*

字符串"NONE"或一个 Double，指定粘度系数。默认值为"NONE"。

**返回值**

一个 DamageStabilizationCohesive 对象。

**异常**

RangeError。

### 60.34.2 成员

DamageStabilizationCohesive 对象的成员与 [DamageStabilizationCohesive](pt02ch60pyo34.md#ker-damagestabilizationcohesive-damagestabilizationcohes-cpp) 方法的参数具有相同的名称和描述。

### 60.34.3 对应的分析关键字

| [*DAMAGE STABILIZATION](../key/key-link.md#usb-kws-mdamagestabilization) |
| --- |
