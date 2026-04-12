# 29.88 SaturationDependence object







The SaturationDependence object specifies the dependence of the permeability of a material on the saturation of the wetting liquid.

**Access**

```
import material
mdb.models[*name*].materials[*name*].permeability.saturationDependence
import odbMaterial
session.odbs[*name*].materials[*name*].permeability.saturationDependence
```

### 29.88.1 SaturationDependence(...)

This method creates a SaturationDependence object.

**Path**

```
mdb.models[*name*].materials[*name*].permeability.SaturationDependence
session.odbs[*name*].materials[*name*].permeability.SaturationDependence
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

None.

**Table data**

- ![](../graphics/ker_eqn00362.gif). (Dimensionless.)
- Saturation, ![](../graphics/ker_eqn00234.gif). (Dimensionless.)

**Return value**

A SaturationDependence object.

**Exceptions**

RangeError.

### 29.88.2 setValues(...)

This method modifies the SaturationDependence object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [SaturationDependence](pt01ch29pyo88.md#ker-saturationdependence-saturationdependence-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.88.3 Members

The SaturationDependence object has members with the same names and descriptions as the arguments to the [SaturationDependence](pt01ch29pyo88.md#ker-saturationdependence-saturationdependence-pyc) method.

### 29.88.4 Corresponding analysis keywords

| [*PERMEABILITY](../key/key-link.md#usb-kws-mpermeabil) |
| --- |




