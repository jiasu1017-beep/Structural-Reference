# 63.2 AcousticInfiniteSection object







The AcousticInfiniteSection object defines the properties of an acoustic section.

The AcousticInfiniteSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.2.1 AcousticInfiniteSection(...)

This method creates an AcousticInfiniteSection object.

**Path**

```
sectionApi.AcousticInfiniteSection
```

**Prototype**

```
odb_AcousticInfiniteSection&
AcousticInfiniteSection(const odb_String& name,
                        const odb_String& material,
                        double thickness,
                        int order);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*material*

An odb_String specifying the name of the material.

**Optional arguments**

*thickness*

A Double specifying the thickness of the section. Possible values are *thickness* ![](../graphics/ker_eqn00060.gif) 0.0. The default value is 1.0.

*order*

An Int specifying the number of ninth-order polynomials that will be used to resolve the variation of the acoustic field in the infinite direction. Possible values are 0 ![](../graphics/ker_eqn00048.gif) *order* ![](../graphics/ker_eqn00013.gif) 10. The default value is 10.

**Return value**

An AcousticInfiniteSection object.

**Exceptions**

InvalidNameError and RangeError.

### 63.2.2 Members

The AcousticInfiniteSection object has members with the same names and descriptions as the arguments to the [AcousticInfiniteSection](pt02ch63pyo02.md#ker-acousticinfinitesection-acousticinfinitesection-cpp) method.

### 63.2.3 Corresponding analysis keywords

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |




