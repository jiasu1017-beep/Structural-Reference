# 63.14 HomogeneousSolidSection object







The HomogeneousSolidSection object defines the properties of a solid section.

The HomogeneousSolidSection object is derived from the [SolidSection](pt02ch63pyo22.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.14.1 HomogeneousSolidSection(...)

This method creates a HomogeneousSolidSection object.

**Path**

```
sectionApi.HomogeneousSolidSection
```

**Prototype**

```
odb_HomogeneousSolidSection&
HomogeneousSolidSection(const odb_String& name,
                        const odb_String& material,
                        odb_Union thickness);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*material*

An odb_String specifying the name of the material.

**Optional argument**

*thickness*

The string "NONE" or a Double specifying the thickness of the section. Possible values are None or a floating point value such that*thickness* ![](../graphics/ker_eqn00060.gif) 0.0. The default value is "None".

**Return value**

A HomogeneousSolidSection object.

**Exceptions**

InvalidNameError and RangeError.

### 63.14.2 Members

The HomogeneousSolidSection object has members with the same names and descriptions as the arguments to the [HomogeneousSolidSection](pt02ch63pyo14.md#ker-homogeneoussolidsection-homogeneoussolidsection-cpp) method.

### 63.14.3 Corresponding analysis keywords

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |




