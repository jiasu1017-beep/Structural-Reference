# 29.2 AcousticMedium object







The AcousticMedium object specifies the acoustic properties of a material.

**Access**

```
import material
mdb.models[*name*].materials[*name*].acousticMedium
import odbMaterial
session.odbs[*name*].materials[*name*].acousticMedium
```

### 29.2.1 AcousticMedium(...)

This method creates an AcousticMedium object.

**Path**

```
mdb.models[*name*].materials[*name*].AcousticMedium
session.odbs[*name*].materials[*name*].AcousticMedium
```

**Required arguments**

None.

**Optional arguments**

*acousticVolumetricDrag*

A Boolean specifying whether the volumetricTable data is specified. The default value is OFF.

*temperatureDependencyB*

A Boolean specifying whether the data in *bulkTable* depend on temperature. The default value is OFF.

*temperatureDependencyV*

A Boolean specifying whether the data in *volumetricTable* depend on temperature. The default value is OFF.

*dependenciesB*

An Int specifying the number of field variable dependencies for the data in *bulkTable*. The default value is 0.

*dependenciesV*

An Int specifying the number of field variable dependencies for the data in *volumetricTable*. The default value is 0.

*bulkTable*

A sequence of sequences of Floats specifying the following:
- Bulk modulus.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

The default value is an empty sequence.

*volumetricTable*

A sequence of sequences of Floats specifying the following:
- Volumetric drag.
- Frequency.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

The default value is an empty sequence.

**Return value**

An AcousticMedium object.

**Exceptions**

RangeError.

### 29.2.2 setValues(...)

This method modifies the AcousticMedium object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [AcousticMedium](pt01ch29pyo02.md#ker-acousticmedium-acousticmedium-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.2.3 Members

The AcousticMedium object has members with the same names and descriptions as the arguments to the [AcousticMedium](pt01ch29pyo02.md#ker-acousticmedium-acousticmedium-pyc) method.

### 29.2.4 Corresponding analysis keywords

| [*ACOUSTIC MEDIUM](../key/key-link.md#usb-kws-macousticmed) |
| --- |




