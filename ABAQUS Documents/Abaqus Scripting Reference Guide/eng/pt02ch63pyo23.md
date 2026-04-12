# 63.23 SurfaceSection object







The SurfaceSection object defines the properties of a surface section.

The SurfaceSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.23.1 SurfaceSection(...)

This method creates a SurfaceSection object.

**Path**

```
sectionApi.SurfaceSection
```

**Prototype**

```
odb_SurfaceSection&
SurfaceSection(const odb_String& name,
               bool useDensity,
               double density);
```

**Required argument**

*name*

An odb_String specifying the repository key.

**Optional arguments**

*useDensity*

A Boolean specifying whether or not to use the value of *density*. The default value is false.

*density*

A Double specifying the value of density to apply to this section. The default value is 0.0.

**Return value**

A SurfaceSection object.

**Exceptions**

RangeError and InvalidNameError.

### 63.23.2 Members

The SurfaceSection object has members with the same names and descriptions as the arguments to the [SurfaceSection](pt02ch63pyo23.md#ker-surfacesection-surfacesection-cpp) method.

In addition, the SurfaceSection object can have the following member:

**Prototype**

```
odb_RebarLayers rebarLayers() const;
```

*rebarLayers*

A [RebarLayers](pt02ch63pyo19.md) object specifying reinforcement properties.

### 63.23.3 Corresponding analysis keywords

| [*SURFACE SECTION](../key/key-link.md#usb-kws-msurfacesection) |
| --- |




