# 46.23 SurfaceSection object







The SurfaceSection object defines the properties of a surface section.

The SurfaceSection object is derived from the [Section](pt01ch46pyo01.md) object.

**Access**

```
import section
mdb.models[*name*].sections[*name*]
import odbSection
session.odbs[*name*].sections[*name*]
```

### 46.23.1 SurfaceSection(...)

This method creates a SurfaceSection object.

**Path**

```
mdb.models[*name*].SurfaceSection
session.odbs[*name*].SurfaceSection
```

**Required argument**

*name*

A String specifying the repository key.

**Optional arguments**

*useDensity*

A Boolean specifying whether or not to use the value of *density*. The default value is OFF.

*density*

A Float specifying the value of density to apply to this section. The default value is 0.0.

**Return value**

A SurfaceSection object.

**Exceptions**

RangeError and InvalidNameError.

### 46.23.2 Members

The SurfaceSection object has members with the same names and descriptions as the arguments to the [SurfaceSection](pt01ch46pyo23.md#ker-surfacesection-surfacesection-pyc) method.

In addition, the SurfaceSection object can have the following member:

*rebarLayers*

A [RebarLayers](pt01ch46pyo19.md) object specifying reinforcement properties.

### 46.23.3 Corresponding analysis keywords

| [*SURFACE SECTION](../key/key-link.md#usb-kws-msurfacesection) |
| --- |




