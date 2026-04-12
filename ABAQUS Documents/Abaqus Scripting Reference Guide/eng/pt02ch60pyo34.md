# 60.34 DamageStabilizationCohesive object







The DamageStabilizationCohesive object specifies the viscosity coefficients for the damage model for surface-based cohesive behavior or enriched cohesive behavior.

**Access**

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

This method creates a DamageStabilizationCohesive object.

**Path**

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

**Prototype**

```
odb_DamageStabilizationCohesive&
DamageStabilizationCohesive(odb_Union cohesiveCoeff);
```

**Required arguments**

None.

**Optional argument**

*cohesiveCoeff*

The string "NONE" or a Double specifying the viscosity coefficient. The default value is "NONE".

**Return value**

A DamageStabilizationCohesive object.

**Exceptions**

RangeError.

### 60.34.2 Members

The DamageStabilizationCohesive object has members with the same names and descriptions as the arguments to the [DamageStabilizationCohesive](pt02ch60pyo34.md#ker-damagestabilizationcohesive-damagestabilizationcohes-cpp) method.

### 60.34.3 Corresponding analysis keywords

| [*DAMAGE STABILIZATION](../key/key-link.md#usb-kws-mdamagestabilization) |
| --- |




