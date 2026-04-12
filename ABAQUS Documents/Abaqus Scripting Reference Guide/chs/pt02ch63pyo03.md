# 63.3 AcousticInterfaceSection object







The AcousticInterfaceSection object defines the properties of an acoustic section.

The AcousticInterfaceSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.3.1 AcousticInterfaceSection(...)

This method creates an AcousticInterfaceSection object.

**Path**

```
sectionApi.AcousticInterfaceSection
```

**Prototype**

```
odb_AcousticInterfaceSection&
AcousticInterfaceSection(const odb_String& name,
                         double thickness);
```

**Required argument**

*name*

An odb_String specifying the repository key.

**Optional argument**

*thickness*

A Double specifying the thickness of the section. Possible values are *thickness* ![](../graphics/ker_eqn00060.gif) 0.0. The default value is 1.0.

**Return value**

An AcousticInterfaceSection object.

**Exceptions**

InvalidNameError and RangeError.

### 63.3.2 Members

The AcousticInterfaceSection object has members with the same names and descriptions as the arguments to the [AcousticInterfaceSection](pt02ch63pyo03.md#ker-acousticinterfacesection-acousticinterfacesection-cpp) method.

### 63.3.3 Corresponding analysis keywords

| [*INTERFACE](../key/key-link.md#usb-kws-minterface) |
| --- |




