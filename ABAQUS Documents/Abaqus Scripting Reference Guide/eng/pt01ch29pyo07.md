# 29.7 BrittleShear object







The BrittleShear object specifies the postcracking shear behavior of a material used in a brittle cracking model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].brittleCracking.brittleShear
import odbMaterial
session.odbs[*name*].materials[*name*].brittleCracking.brittleShear
```

### 29.7.1 BrittleShear(...)

This method creates a BrittleShear object.

**Path**

```
mdb.models[*name*].materials[*name*].brittleCracking.BrittleShear
session.odbs[*name*].materials[*name*].brittleCracking.BrittleShear
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*type*

A SymbolicConstant specifying the type of postcracking shear behavior. Possible values are RETENTION_FACTOR and POWER_LAW. The default value is RETENTION_FACTOR.

**Table data**

If *type*=RETENTION_FACTOR the table data specify the following:
- Shear retention factor.
- Crack opening strain.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=POWER_LAW the table data specify the following:- e.
- p.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A BrittleShear object.

**Exceptions**

RangeError.

### 29.7.2 setValues(...)

This method modifies the BrittleShear object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [BrittleShear](pt01ch29pyo07.md#ker-brittleshear-brittleshear-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.7.3 Members

The BrittleShear object has members with the same names and descriptions as the arguments to the [BrittleShear](pt01ch29pyo07.md#ker-brittleshear-brittleshear-pyc) method.

### 29.7.4 Corresponding analysis keywords

| [*BRITTLE SHEAR](../key/key-link.md#usb-kws-mbrittleshear) |
| --- |




