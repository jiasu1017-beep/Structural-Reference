# 29.6 BrittleFailure object







The BrittleFailure object specifies the brittle failure of the material.

**Access**

```
import material
mdb.models[*name*].materials[*name*].brittleCracking.brittleFailure
import odbMaterial
session.odbs[*name*].materials[*name*].brittleCracking.brittleFailure
```

### 29.6.1 BrittleFailure(...)

This method creates a BrittleFailure object.

**Path**

```
mdb.models[*name*].materials[*name*].brittleCracking.BrittleFailure
session.odbs[*name*].materials[*name*].brittleCracking.BrittleFailure
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*failureCriteria*

A SymbolicConstant specifying the failure criteria. Possible values are UNIDIRECTIONAL, BIDIRECTIONAL, and TRIDIRECTIONAL. The default value is UNIDIRECTIONAL.

**Table data**

If parent [BrittleCracking](pt01ch29pyo05.md) member *type*=STRAIN the table data specify the following:
- Direct cracking failure strain.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If parent [BrittleCracking](pt01ch29pyo05.md) member *type*=DISPLACEMENT or *type*=GFI the table data specify the following:- Direct cracking failure displacement.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A BrittleFailure object.

**Exceptions**

RangeError.

### 29.6.2 setValues(...)

This method modifies the BrittleFailure object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [BrittleFailure](pt01ch29pyo06.md#ker-brittlefailure-brittlefailure-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.6.3 Members

The BrittleFailure object has members with the same names and descriptions as the arguments to the [BrittleFailure](pt01ch29pyo06.md#ker-brittlefailure-brittlefailure-pyc) method.

### 29.6.4 Corresponding analysis keywords

| [*BRITTLE FAILURE](../key/key-link.md#usb-kws-mbrittlefailure) |
| --- |




