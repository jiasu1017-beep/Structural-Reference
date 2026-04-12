# 63.26 TrussSection object







The TrussSection object defines the properties of a truss section.

The TrussSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.26.1 TrussSection(...)

This method creates a TrussSection object.

**Path**

```
sectionApi.TrussSection
```

**Prototype**

```
odb_TrussSection&
TrussSection(const odb_String& name,
             const odb_String& material,
             double area);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*material*

An odb_String specifying the name of the material.

**Optional argument**

*area*

A Double specifying the cross-sectional area for the section. Possible values are *area* ![](../graphics/ker_eqn00060.gif) 0. The default value is 1.0.

**Return value**

A TrussSection object.

**Exceptions**

RangeError and InvalidNameError.

### 63.26.2 Members

The TrussSection object has members with the same names and descriptions as the arguments to the [TrussSection](pt02ch63pyo26.md#ker-trusssection-trusssection-cpp) method.

### 63.26.3 Corresponding analysis keywords

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |




