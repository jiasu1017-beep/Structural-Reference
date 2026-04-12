# 29.57 GasketTransverseShearElastic object







The GasketTransverseShearElastic object defines the elastic parameters for the transverse shear behavior of a gasket.

**Access**

```
import material
mdb.models[*name*].materials[*name*].gasketTransverseShearElastic
import odbMaterial
session.odbs[*name*].materials[*name*].gasketTransverseShearElastic
```

### 29.57.1 GasketTransverseShearElastic(...)

This method creates a GasketTransverseShearElastic object.

**Path**

```
mdb.models[*name*].materials[*name*].GasketTransverseShearElastic
session.odbs[*name*].materials[*name*].GasketTransverseShearElastic
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*variableUnits*

A SymbolicConstant specifying the unit system in which the transverse shear behavior will be defined. Possible values are STRESS and FORCE. The default value is STRESS.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Shear stiffness. (This value cannot be negative.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A GasketTransverseShearElastic object.

**Exceptions**

RangeError.

### 29.57.2 setValues(...)

This method modifies the GasketTransverseShearElastic object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [GasketTransverseShearElastic](pt01ch29pyo57.md#ker-gaskettransverseshearelastic-gaskettransverseshearel-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.57.3 Members

The GasketTransverseShearElastic object has members with the same names and descriptions as the arguments to the [GasketTransverseShearElastic](pt01ch29pyo57.md#ker-gaskettransverseshearelastic-gaskettransverseshearel-pyc) method.

### 29.57.4 Corresponding analysis keywords

| [*GASKET ELASTICITY](../key/key-link.md#usb-kws-mgasketelastic) |
| --- |




