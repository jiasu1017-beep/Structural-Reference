# 29.68 MagneticPermeability object







The MagneticPermeability object specifies magnetic permeability.

**Access**

```
import material
mdb.models[*name*].materials[*name*].magneticPermeability
import odbMaterial
session.odbs[*name*].materials[*name*].magneticPermeability
```

### 29.68.1 MagneticPermeability(...)

This method creates an MagneticPermeability object.

**Path**

```
mdb.models[*name*].materials[*name*].MagneticPermeability
session.odbs[*name*].materials[*name*].MagneticPermeability
```

**Required arguments**

*table*

A sequence of sequences of Floats specifying the items described below.

*table2*

A sequence of sequences of Floats specifying if Nonlinear BH option is true, table2 must be specified. The items of table2 are similar to that of table but for second direction.

*table3*

A sequence of sequences of Floats specifying if Nonlinear BH option is true, table3 must be specified. The items of table3 are similar to that of table but for third direction.

**Optional arguments**

*type*

A SymbolicConstant specifying the type of magnetic permeability. Possible values are ISOTROPIC, ORTHOTROPIC, and ANISOTROPIC. The default value is ISOTROPIC.

*frequencyDependency*

A Boolean specifying whether the data depend on frequency. The default value is OFF.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*nonlinearBH*

A Boolean specifying whether the magnetic behavior is nonlinear and available in tabular form of magnetic flux density versus magnetic field values. The default value is OFF.

**Table data**

If *type*=ISOTROPIC, the table data specify the following:
- Magnetic permeability.
- Frequency, if the data depend on frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ISOTROPIC, 					 and *nonlinearBH*=TRUE, the table data specify the following:- Magntitude of the magnetic flux density vector.
- Magnitude of the magnetic field vector.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ORTHOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00221.gif).
- ![](../graphics/ker_eqn00222.gif).
- ![](../graphics/ker_eqn00223.gif).
- Frequency, if the data depend on frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ANISOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00221.gif).
- ![](../graphics/ker_eqn00224.gif).
- ![](../graphics/ker_eqn00222.gif).
- ![](../graphics/ker_eqn00225.gif).
- ![](../graphics/ker_eqn00226.gif).
- ![](../graphics/ker_eqn00223.gif).
- Frequency, if the data depend on frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ANISOTROPIC,                       and *nonlinearBH*=TRUE, the table data specify the following:- Magntitude of the magnetic flux density vector in the first direction.
- Magnitude of the magnetic field vector in the second direction.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A MagneticPermeability object.

**Exceptions**

RangeError.

### 29.68.2 setValues(...)

This method modifies the MagneticPermeability object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [MagneticPermeability](pt01ch29pyo68.md#ker-magneticpermeability-magneticpermeability-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.68.3 Members

The MagneticPermeability object has members with the same names and descriptions as the arguments to the [MagneticPermeability](pt01ch29pyo68.md#ker-magneticpermeability-magneticpermeability-pyc) method.

### 29.68.4 Corresponding analysis keywords

| [*MAGNETIC PERMEABILITY](../key/key-link.md#usb-kws-mmagpermeability) |
| --- |




