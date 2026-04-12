# 29.34 DamageStabilizationCohesive object







The DamageStabilizationCohesive object specifies the viscosity coefficients for the damage model for surface-based cohesive behavior or enriched cohesive behavior.

**Access**

```
import material
mdb.models[*name*].materials[*name*].ductileDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].fldDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].flsdDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].hashinDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].johnsonCookDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].maxeDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].maxpeDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].maxpsDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].maxsDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].mkDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].msfldDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].quadeDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].quadsDamageInitiation\
.damageStabilizationCohesive
mdb.models[*name*].materials[*name*].shearDamageInitiation\
.damageStabilizationCohesive
import odbMaterial
session.odbs[*name*].materials[*name*].ductileDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].fldDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].flsdDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].hashinDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].johnsonCookDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].maxeDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].maxpeDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].maxpsDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].maxsDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].mkDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].msfldDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].quadeDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].quadsDamageInitiation\
.damageStabilizationCohesive
session.odbs[*name*].materials[*name*].shearDamageInitiation\
.damageStabilizationCohesive
```

### 29.34.1 DamageStabilizationCohesive(...)

This method creates a DamageStabilizationCohesive object.

**Path**

```
mdb.models[*name*].materials[*name*].ductileDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].fldDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].flsdDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].hashinDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].johnsonCookDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].maxeDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].maxpeDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].maxpsDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].maxsDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].mkDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].msfldDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].quadeDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].quadsDamageInitiation\
.DamageStabilizationCohesive
mdb.models[*name*].materials[*name*].shearDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].ductileDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].fldDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].flsdDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].hashinDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].johnsonCookDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].maxeDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].maxpeDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].maxpsDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].maxsDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].mkDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].msfldDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].quadeDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].quadsDamageInitiation\
.DamageStabilizationCohesive
session.odbs[*name*].materials[*name*].shearDamageInitiation\
.DamageStabilizationCohesive
```

**Required arguments**

None.

**Optional argument**

*cohesiveCoeff*

 `None` or a Float specifying the viscosity coefficient. The default value is `None`.

**Return value**

A DamageStabilizationCohesive object.

**Exceptions**

RangeError.

### 29.34.2 setValues(...)

This method modifies the DamageStabilizationCohesive object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DamageStabilizationCohesive](pt01ch29pyo34.md#ker-damagestabilizationcohesive-damagestabilizationcohes-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.34.3 Members

The DamageStabilizationCohesive object has members with the same names and descriptions as the arguments to the [DamageStabilizationCohesive](pt01ch29pyo34.md#ker-damagestabilizationcohesive-damagestabilizationcohes-pyc) method.

### 29.34.4 Corresponding analysis keywords

| [*DAMAGE STABILIZATION](../key/key-link.md#usb-kws-mdamagestabilization) |
| --- |




