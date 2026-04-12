# 29.8 CapCreepCohesion object







The CapCreepCohesion object specifies a cap creep model and material properties.

**Access**

```
import material
mdb.models[*name*].materials[*name*].capPlasticity.capCreepCohesion
import odbMaterial
session.odbs[*name*].materials[*name*].capPlasticity.capCreepCohesion
```

### 29.8.1 CapCreepCohesion(...)

This method creates a CapCreepCohesion object.

**Path**

```
mdb.models[*name*].materials[*name*].capPlasticity.CapCreepCohesion
session.odbs[*name*].materials[*name*].capPlasticity.CapCreepCohesion
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*law*

A SymbolicConstant specifying the cap creep law. Possible values are STRAIN, TIME, SINGHM, and USER. The default value is STRAIN.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *law*=STRAIN or *law*=TIME, the table data specify the following:
- ![](../graphics/ker_eqn00010.gif).
- ![](../graphics/ker_eqn00088.gif).
- ![](../graphics/ker_eqn00089.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *law*=SINGHM, the table data specify the following:- ![](../graphics/ker_eqn00010.gif).
- ![](../graphics/ker_eqn00090.gif).
- ![](../graphics/ker_eqn00089.gif).
- ![](../graphics/ker_eqn00091.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CapCreepCohesion object.

**Exceptions**

None.

### 29.8.2 setValues(...)

This method modifies the CapCreepCohesion object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CapCreepCohesion](pt01ch29pyo08.md#ker-capcreepcohesion-capcreepcohesion-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.8.3 Members

The CapCreepCohesion object has members with the same names and descriptions as the arguments to the [CapCreepCohesion](pt01ch29pyo08.md#ker-capcreepcohesion-capcreepcohesion-pyc) method.

### 29.8.4 Corresponding analysis keywords

| [*CAP CREEP](../key/key-link.md#usb-kws-mcapcreep) |
| --- |




