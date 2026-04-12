# 60.67 LowDensityFoam object







The LowDensityFoam object specifies properties for low-density foam.

**Access**

```
materialApi.materials()[*name*].lowDensityFoam()
```

### 60.67.1 LowDensityFoam(...)

This method creates a LowDensityFoam object.

**Path**

```
materialApi.materials()[*name*].LowDensityFoam
```

**Prototype**

```
odb_LowDensityFoam&
LowDensityFoam(bool elementRemoval,
               odb_Union maxAllowablePrincipalStress,
               bool extrapolateStressStrainCurve,
               const odb_String& strainRateType,
               double mu0,
               double mu1,
               double alpha);
```

**Required arguments**

None.

**Optional arguments**

*elementRemoval*

A Boolean specifying whether elements are removed if exceeding maximum principal tensile stress. This argument is valid only when *maxAllowablePrincipalStress* is defined. The default value is false.

*maxAllowablePrincipalStress*

The string "NONE" or a Double specifying the maximum allowable principal tensile stress. The default value is "NONE".

*extrapolateStressStrainCurve*

A Boolean specifying whether the stress-strain curve is extrapolated if exceeding maximum strain rate. The default value is false.

*strainRateType*

An odb_String specifying strain rate measure used for constitutive calculations. Possible values are "PRINCIPAL" and "VOLUMETRIC". The default value is "VOLUMETRIC".

*mu0*

A Double specifying the relaxation coefficient ![](../graphics/ker_eqn00288.gif). The default value is 10–4.

*mu1*

A Double specifying the relaxation coefficient ![](../graphics/ker_eqn00070.gif). The default value is 0.510–2.

*alpha*

A Double specifying the relaxation coefficient ![](../graphics/ker_eqn00090.gif). The default value is 2.0.

**Return value**

A LowDensityFoam object.

**Exceptions**

RangeError.

### 60.67.2 Members

The LowDensityFoam object has members with the same names and descriptions as the arguments to the [LowDensityFoam](pt02ch60pyo67.md#ker-lowdensityfoam-lowdensityfoam-cpp) method.

In addition, the LowDensityFoam object can have the following members:

**Prototype**

```
odb_UniaxialTestData uniaxialTensionTestData() const;
odb_UniaxialTestData uniaxialCompressionTestData() const;
```

*uniaxialTensionTestData*

A [UniaxialTestData](pt02ch60pyo101.md) object.

*uniaxialCompressionTestData*

A [UniaxialTestData](pt02ch60pyo101.md) object.

### 60.67.3 Corresponding analysis keywords

| [*LOW DENSITY FOAM](../key/key-link.md#usb-kws-mlowdensfoam) |
| --- |




