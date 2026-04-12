# 29.67 LowDensityFoam object







The LowDensityFoam object specifies properties for low-density foam.

**Access**

```
import material
mdb.models[*name*].materials[*name*].lowDensityFoam
import odbMaterial
session.odbs[*name*].materials[*name*].lowDensityFoam
```

### 29.67.1 LowDensityFoam(...)

This method creates a LowDensityFoam object.

**Path**

```
mdb.models[*name*].materials[*name*].LowDensityFoam
session.odbs[*name*].materials[*name*].LowDensityFoam
```

**Required arguments**

None.

**Optional arguments**

*elementRemoval*

A Boolean specifying whether elements are removed if exceeding maximum principal tensile stress. This argument is valid only when *maxAllowablePrincipalStress* is defined. The default value is OFF.

*maxAllowablePrincipalStress*

 `None` or a Float specifying the maximum allowable principal tensile stress. The default value is `None`.

*extrapolateStressStrainCurve*

A Boolean specifying whether the stress-strain curve is extrapolated if exceeding maximum strain rate. The default value is OFF.

*strainRateType*

A SymbolicConstant specifying strain rate measure used for constitutive calculations. Possible values are PRINCIPAL and VOLUMETRIC. The default value is VOLUMETRIC.

*mu0*

A Float specifying the relaxation coefficient ![](../graphics/ker_eqn00288.gif). The default value is 10–4.

*mu1*

A Float specifying the relaxation coefficient ![](../graphics/ker_eqn00070.gif). The default value is 0.510–2.

*alpha*

A Float specifying the relaxation coefficient ![](../graphics/ker_eqn00090.gif). The default value is 2.0.

**Return value**

A LowDensityFoam object.

**Exceptions**

RangeError.

### 29.67.2 setValues(...)

This method modifies the LowDensityFoam object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [LowDensityFoam](pt01ch29pyo67.md#ker-lowdensityfoam-lowdensityfoam-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.67.3 Members

The LowDensityFoam object has members with the same names and descriptions as the arguments to the [LowDensityFoam](pt01ch29pyo67.md#ker-lowdensityfoam-lowdensityfoam-pyc) method.

In addition, the LowDensityFoam object can have the following members:

*uniaxialTensionTestData*

A [UniaxialTestData](pt01ch29pyo101.md) object.

*uniaxialCompressionTestData*

A [UniaxialTestData](pt01ch29pyo101.md) object.

### 29.67.4 Corresponding analysis keywords

| [*LOW DENSITY FOAM](../key/key-link.md#usb-kws-mlowdensfoam) |
| --- |




