# 29.37 Density object







The Density object specifies the material density.

**Access**

```
import material
mdb.models[*name*].materials[*name*].density
import odbMaterial
session.odbs[*name*].materials[*name*].density
```

### 29.37.1 Density(...)

This method creates a Density object.

**Path**

```
mdb.models[*name*].materials[*name*].Density
session.odbs[*name*].materials[*name*].Density
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*distributionType*

A SymbolicConstant specifying how the density is distributed spatially. Possible values are UNIFORM, ANALYTICAL_FIELD, and DISCRETE_FIELD. The default value is UNIFORM.

*fieldName*

A String specifying the name of the [AnalyticalField](pt01ch21pyo02.md) or [DiscreteField](pt01ch21pyo04.md) object associated with this material option. The *fieldName* argument applies only when *distributionType*=ANALYTICAL_FIELD or *distributionType*=DISCRETE_FIELD. The default value is an empty string.

**Table data**

- The mass density.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Density object.

**Exceptions**

RangeError.

### 29.37.2 setValues(...)

This method modifies the Density object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Density](pt01ch29pyo37.md#ker-density-density-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.37.3 Members

The Density object has members with the same names and descriptions as the arguments to the [Density](pt01ch29pyo37.md#ker-density-density-pyc) method.

### 29.37.4 Corresponding analysis keywords

| [*DENSITY](../key/key-link.md#usb-kws-mdensity) |
| --- |




