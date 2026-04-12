# 29.95 SpecificHeat object







The SpecificHeat object specifies a material's specific heat.

**Access**

```
import material
mdb.models[*name*].materials[*name*].specificHeat
import odbMaterial
session.odbs[*name*].materials[*name*].specificHeat
```

### 29.95.1 SpecificHeat(...)

This method creates a SpecificHeat object.

**Path**

```
mdb.models[*name*].materials[*name*].SpecificHeat
session.odbs[*name*].materials[*name*].SpecificHeat
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*law*

A SymbolicConstant specifying the specific heat behavior. Possible values are CONSTANTVOLUME and CONSTANTPRESSURE. The default value is CONSTANTVOLUME.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Specific heat per unit mass.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A SpecificHeat object.

**Exceptions**

RangeError.

### 29.95.2 setValues(...)

This method modifies the SpecificHeat object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SpecificHeat](pt01ch29pyo95.md#ker-specificheat-specificheat-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.95.3 Members

The SpecificHeat object has members with the same names and descriptions as the arguments to the [SpecificHeat](pt01ch29pyo95.md#ker-specificheat-specificheat-pyc) method.

### 29.95.4 Corresponding analysis keywords

| [*SPECIFIC HEAT](../key/key-link.md#usb-kws-mspecificheat) |
| --- |




