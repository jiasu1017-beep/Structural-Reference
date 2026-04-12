# 29.18 Concrete object







The Concrete object defines concrete properties beyond the elastic range.

**Access**

```
import material
mdb.models[*name*].materials[*name*].concrete
import odbMaterial
session.odbs[*name*].materials[*name*].concrete
```

### 29.18.1 Concrete(...)

This method creates a Concrete object.

**Path**

```
mdb.models[*name*].materials[*name*].Concrete
session.odbs[*name*].materials[*name*].Concrete
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

- Absolute value of compressive stress.
- Absolute value of plastic strain.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Concrete object.

**Exceptions**

RangeError.

### 29.18.2 setValues(...)

This method modifies the Concrete object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Concrete](pt01ch29pyo18.md#ker-concrete-concrete-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.18.3 Members

The Concrete object has members with the same names and descriptions as the arguments to the [Concrete](pt01ch29pyo18.md#ker-concrete-concrete-pyc) method.

In addition, the Concrete object can have the following members:

*failureRatios*

A [FailureRatios](pt01ch29pyo52.md) object.

*shearRetention*

A [ShearRetention](pt01ch29pyo89.md) object.

*tensionStiffening*

A [TensionStiffening](pt01ch29pyo98.md) object.

### 29.18.4 Corresponding analysis keywords

| [*CONCRETE](../key/key-link.md#usb-kws-mconcrete) |
| --- |




