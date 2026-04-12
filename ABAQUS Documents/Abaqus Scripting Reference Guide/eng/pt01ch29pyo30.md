# 29.30 CyclicHardening object







The CyclicHardening object defines the evolution of the elastic domain for the nonlinear isotropic/kinematic hardening model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].plastic.cyclicHardening
import odbMaterial
session.odbs[*name*].materials[*name*].plastic.cyclicHardening
```

### 29.30.1 CyclicHardening(...)

This method creates a CyclicHardening object.

**Path**

```
mdb.models[*name*].materials[*name*].plastic.CyclicHardening
session.odbs[*name*].materials[*name*].plastic.CyclicHardening
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*parameters*

A Boolean specifying whether material parameters are to be input directly. The default value is OFF.

**Table data**

- Equivalent stress.
- ![](../graphics/ker_eqn00160.gif) (only if *parameters*=ON).
- Hardening parameter (only if *parameters*=ON).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CyclicHardening object.

**Exceptions**

None.

### 29.30.2 setValues(...)

This method modifies the CyclicHardening object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CyclicHardening](pt01ch29pyo30.md#ker-cyclichardening-cyclichardening-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.30.3 Members

The CyclicHardening object has members with the same names and descriptions as the arguments to the [CyclicHardening](pt01ch29pyo30.md#ker-cyclichardening-cyclichardening-pyc) method.

### 29.30.4 Corresponding analysis keywords

| [*CYCLIC HARDENING](../key/key-link.md#usb-kws-mcyclichardening) |
| --- |




