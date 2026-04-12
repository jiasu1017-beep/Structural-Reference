# 29.91 SimpleShearTestData object







The SimpleShearTestData object provides simple shear test data.

**Access**

```
import material
mdb.models[*name*].materials[*name*].hyperfoam.simpleShearTestData
import odbMaterial
session.odbs[*name*].materials[*name*].hyperfoam.simpleShearTestData
```

### 29.91.1 SimpleShearTestData(...)

This method creates a SimpleShearTestData object.

**Path**

```
mdb.models[*name*].materials[*name*].hyperfoam.SimpleShearTestData
session.odbs[*name*].materials[*name*].hyperfoam.SimpleShearTestData
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

None.

**Table data**

- Nominal shear stress, ![](../graphics/ker_eqn00332.gif).
- Nominal shear strain, ![](../graphics/ker_eqn00040.gif).
- Nominal transverse stress, ![](../graphics/ker_eqn00366.gif) (normal to edge with shear stress). This stress value is optional.

**Return value**

A SimpleShearTestData object.

**Exceptions**

None.

### 29.91.2 setValues(...)

This method modifies the SimpleShearTestData object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SimpleShearTestData](pt01ch29pyo91.md#ker-simplesheartestdata-simplesheartestdata-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.91.3 Members

The SimpleShearTestData object has members with the same names and descriptions as the arguments to the [SimpleShearTestData](pt01ch29pyo91.md#ker-simplesheartestdata-simplesheartestdata-pyc) method.

### 29.91.4 Corresponding analysis keywords

| [*SIMPLE SHEAR TEST DATA](../key/key-link.md#usb-kws-msimplesheartestdata) |
| --- |




