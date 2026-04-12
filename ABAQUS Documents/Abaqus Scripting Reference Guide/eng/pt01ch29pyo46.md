# 29.46 ElectricalConductivity object







The ElectricalConductivity object specifies electrical conductivity.

**Access**

```
import material
mdb.models[*name*].materials[*name*].electricalConductivity
import odbMaterial
session.odbs[*name*].materials[*name*].electricalConductivity
```

### 29.46.1 ElectricalConductivity(...)

This method creates an ElectricalConductivity object.

**Path**

```
mdb.models[*name*].materials[*name*].ElectricalConductivity
session.odbs[*name*].materials[*name*].ElectricalConductivity
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*type*

A SymbolicConstant specifying the type of electrical conductivity. Possible values are ISOTROPIC, ORTHOTROPIC, and ANISOTROPIC. The default value is ISOTROPIC.

*frequencyDependency*

A Boolean specifying whether the data depend on frequency. The default value is OFF.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=ISOTROPIC, the table data specify the following:
- Electrical conductivity.
- Frequency, if the data depend on frequency.
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

**Return value**

An ElectricalConductivity object.

**Exceptions**

RangeError.

### 29.46.2 setValues(...)

This method modifies the ElectricalConductivity object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ElectricalConductivity](pt01ch29pyo46.md#ker-electricalconductivity-electricalconductivity-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.46.3 Members

The ElectricalConductivity object has members with the same names and descriptions as the arguments to the [ElectricalConductivity](pt01ch29pyo46.md#ker-electricalconductivity-electricalconductivity-pyc) method.

### 29.46.4 Corresponding analysis keywords

| [*ELECTRICAL CONDUCTIVITY](../key/key-link.md#usb-kws-melectricconduct) |
| --- |




