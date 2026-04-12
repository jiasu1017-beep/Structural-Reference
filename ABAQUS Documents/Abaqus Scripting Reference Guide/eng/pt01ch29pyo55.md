# 29.55 GasketMembraneElastic object







The GasketMembraneElastic object defines the elastic parameters for the membrane shear behavior of a gasket.

**Access**

```
import material
mdb.models[*name*].materials[*name*].gasketMembraneElastic
import odbMaterial
session.odbs[*name*].materials[*name*].gasketMembraneElastic
```

### 29.55.1 GasketMembraneElastic(...)

This method creates a GasketMembraneElastic object.

**Path**

```
mdb.models[*name*].materials[*name*].GasketMembraneElastic
session.odbs[*name*].materials[*name*].GasketMembraneElastic
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Young's modulus, ![](../graphics/ker_eqn00163.gif).
- Poisson's ratio, ![](../graphics/ker_eqn00164.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A GasketMembraneElastic object.

**Exceptions**

RangeError.

### 29.55.2 setValues(...)

This method modifies the GasketMembraneElastic object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [GasketMembraneElastic](pt01ch29pyo55.md#ker-gasketmembraneelastic-gasketmembraneelastic-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.55.3 Members

The GasketMembraneElastic object has members with the same names and descriptions as the arguments to the [GasketMembraneElastic](pt01ch29pyo55.md#ker-gasketmembraneelastic-gasketmembraneelastic-pyc) method.

### 29.55.4 Corresponding analysis keywords

| [*GASKET ELASTICITY](../key/key-link.md#usb-kws-mgasketelastic) |
| --- |




