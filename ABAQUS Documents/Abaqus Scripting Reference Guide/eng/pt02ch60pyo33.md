# 60.33 DamageStabilization object







The DamageStabilization object specifies the viscosity coefficients for the damage model for fiber-reinforced materials.

**Access**

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

This method creates a DamageStabilization object.

**Path**

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

**Prototype**

```
odb_DamageStabilization&
DamageStabilization(double fiberTensileCoeff,
                    double fiberCompressiveCoeff,
                    double matrixTensileCoeff,
                    double matrixCompressiveCoeff);
```

**Required arguments**

*fiberTensileCoeff*

A Double specifying the viscosity coefficient for the fiber tensile failure mode.

*fiberCompressiveCoeff*

A Double specifying the viscosity coefficient for the fiber compressive failure mode.

*matrixTensileCoeff*

A Double specifying the viscosity coefficient for the matrix tensile failure mode.

*matrixCompressiveCoeff*

A Double specifying the viscosity coefficient for the matrix compressive failure mode.

**Optional arguments**

None.

**Return value**

A DamageStabilization object.

**Exceptions**

RangeError.

### 60.33.2 Members

The DamageStabilization object has members with the same names and descriptions as the arguments to the [DamageStabilization](pt02ch60pyo33.md#ker-damagestabilization-damagestabilization-cpp) method.

### 60.33.3 Corresponding analysis keywords

| [*DAMAGE STABILIZATION](../key/key-link.md#usb-kws-mdamagestabilization) |
| --- |




