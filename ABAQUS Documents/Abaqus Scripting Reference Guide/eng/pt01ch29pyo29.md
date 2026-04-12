# 29.29 CycledPlastic object







The CycledPlastic object specifies cycled yield stress data for the ORNL constitutive model.

**Access**

```
import material
mdb.models[*name*].materials[*name*].plastic.cycledPlastic
import odbMaterial
session.odbs[*name*].materials[*name*].plastic.cycledPlastic
```

### 29.29.1 CycledPlastic(...)

This method creates a CycledPlastic object.

**Path**

```
mdb.models[*name*].materials[*name*].plastic.CycledPlastic
session.odbs[*name*].materials[*name*].plastic.CycledPlastic
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional argument**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

**Table data**

- Yield stress.
- Plastic strain.
- Temperature, if the data depend on temperature.

**Return value**

A CycledPlastic object.

**Exceptions**

None.

### 29.29.2 setValues(...)

This method modifies the CycledPlastic object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CycledPlastic](pt01ch29pyo29.md#ker-cycledplastic-cycledplastic-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.29.3 Members

The CycledPlastic object has members with the same names and descriptions as the arguments to the [CycledPlastic](pt01ch29pyo29.md#ker-cycledplastic-cycledplastic-pyc) method.

### 29.29.4 Corresponding analysis keywords

| [*CYCLED PLASTIC](../key/key-link.md#usb-kws-mcycledplastic) |
| --- |




