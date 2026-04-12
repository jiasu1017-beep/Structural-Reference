# 29.98 TensionStiffening object







The TensionStiffening object defines the retained tensile stress normal to a crack in a [Concrete](pt01ch29pyo18.md) model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].concrete.tensionStiffening
import odbMaterial
session.odbs[*name*].materials[*name*].concrete.tensionStiffening
```

### 29.98.1 TensionStiffening(...)

This method creates a TensionStiffening object.

**Path**

```
mdb.models[*name*].materials[*name*].concrete.TensionStiffening
session.odbs[*name*].materials[*name*].concrete.TensionStiffening
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*type*

A SymbolicConstant specifying how the postcracking behavior is defined. Possible values are DISPLACEMENT and STRAIN. The default value is STRAIN.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=STRAIN, the table data specify the following:
- Fraction of remaining stress to stress at cracking.
- Absolute value of the direct strain minus the direct strain at cracking.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=DISPLACEMENT, the table data specify the following:- Displacement, ![](../graphics/ker_eqn00372.gif), at which a linear loss of strength after cracking gives zero stress.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A TensionStiffening object.

**Exceptions**

RangeError.

### 29.98.2 setValues(...)

This method modifies the TensionStiffening object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [TensionStiffening](pt01ch29pyo98.md#ker-tensionstiffening-tensionstiffening-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.98.3 Members

The TensionStiffening object has members with the same names and descriptions as the arguments to the [TensionStiffening](pt01ch29pyo98.md#ker-tensionstiffening-tensionstiffening-pyc) method.

### 29.98.4 Corresponding analysis keywords

| [*TENSION STIFFENING](../key/key-link.md#usb-kws-mtensionstiff) |
| --- |




