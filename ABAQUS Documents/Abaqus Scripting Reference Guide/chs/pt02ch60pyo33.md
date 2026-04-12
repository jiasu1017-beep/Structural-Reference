# 60.33 DamageStabilization 对象

DamageStabilization 对象为纤维增强材料的损伤模型指定粘度系数。

**访问**

```
materialApi.materials()[*name*].ductileDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].fldDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].flsdDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].hashinDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].johnsonCookDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].maxeDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].maxpeDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].maxpsDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].maxsDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].mkDamageInitiation().damageStabilization()
materialApi.materials()[*name*].msfldDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].quadeDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].quadsDamageInitiation()\
.damageStabilization()
materialApi.materials()[*name*].shearDamageInitiation()\
.damageStabilization()
```

### 60.33.1 DamageStabilization(...)

此方法创建一个 DamageStabilization 对象。

**路径**

```
materialApi.materials()[*name*].ductileDamageInitiation()\
.DamageStabilization
materialApi.materials()[*name*].fldDamageInitiation().DamageStabilization
materialApi.materials()[*name*].flsdDamageInitiation().DamageStabilization
materialApi.materials()[*name*].hashinDamageInitiation()\
.DamageStabilization
materialApi.materials()[*name*].johnsonCookDamageInitiation()\
.DamageStabilization
materialApi.materials()[*name*].maxeDamageInitiation().DamageStabilization
materialApi.materials()[*name*].maxpeDamageInitiation()\
.DamageStabilization
materialApi.materials()[*name*].maxpsDamageInitiation()\
.DamageStabilization
materialApi.materials()[*name*].maxsDamageInitiation().DamageStabilization
materialApi.materials()[*name*].mkDamageInitiation().DamageStabilization
materialApi.materials()[*name*].msfldDamageInitiation()\
.DamageStabilization
materialApi.materials()[*name*].quadeDamageInitiation()\
.DamageStabilization
materialApi.materials()[*name*].quadsDamageInitiation()\
.DamageStabilization
materialApi.materials()[*name*].shearDamageInitiation()\
.DamageStabilization
```

**原型**

```
odb_DamageStabilization&
DamageStabilization(double fiberTensileCoeff,
                    double fiberCompressiveCoeff,
                    double matrixTensileCoeff,
                    double matrixCompressiveCoeff);
```

**必需参数**

*fiberTensileCoeff*

一个 Double，指定纤维拉伸失效模式的粘度系数。

*fiberCompressiveCoeff*

一个 Double，指定纤维压缩失效模式的粘度系数。

*matrixTensileCoeff*

一个 Double，指定基体拉伸失效模式的粘度系数。

*matrixCompressiveCoeff*

一个 Double，指定基体压缩失效模式的粘度系数。

**可选参数**

无。

**返回值**

一个 DamageStabilization 对象。

**异常**

RangeError。

### 60.33.2 成员

DamageStabilization 对象的成员与 [DamageStabilization](pt02ch60pyo33.md#ker-damagestabilization-damagestabilization-cpp) 方法的参数具有相同的名称和描述。

### 60.33.3 对应的分析关键字

| [*DAMAGE STABILIZATION](../key/key-link.md#usb-kws-mdamagestabilization) |
| --- |
