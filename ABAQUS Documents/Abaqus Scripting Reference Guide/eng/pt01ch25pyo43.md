# 25.43 GeometricProperties object







The GeometricProperties object specifies surface interaction properties.

**Access**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].geometricProperties
```

### 25.43.1 GeometricProperties(...)

This method creates a GeometricProperties object.

**Path**

```
mdb.models[*name*].interactionProperties[*name*].GeometricProperties
```

**Required arguments**

None.

**Optional arguments**

*contactArea*

A Float specifying the out-of-plane thickness of the surface for a two-dimensional model or cross-sectional area for every node in the node-based surface. The default value is 1.0.

*padThickness*

 `None` or a Float specifying the thickness of an interfacial layer between the contacting surfaces.                       If *padThickness*=`None`, there is no interfacial layer. The default value is `None`.

**Return value**

A GeometricProperties object.

**Exceptions**

None.

### 25.43.2 setValues(...)

This method modifies the GeometricProperties object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [GeometricProperties](pt01ch25pyo43.md#ker-geometricproperties-geometricproperties-pyc) method.

**Return value**

None

**Exceptions**

None.

### 25.43.3 Members

The GeometricProperties object has members with the same names and descriptions as the arguments to the [GeometricProperties](pt01ch25pyo43.md#ker-geometricproperties-geometricproperties-pyc) method.

### 25.43.4 Corresponding analysis keywords

| [*SURFACE INTERACTION](../key/key-link.md#usb-kws-hsurfaceinteraction) |
| --- |




