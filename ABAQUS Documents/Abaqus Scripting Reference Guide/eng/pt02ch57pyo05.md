# 57.5 GeneralizedProfile object







The GeneralizedProfile object defines the properties of a profile via its area, moment of inertia, etc.

The GeneralizedProfile object is derived from the [Profile](pt02ch57pyo01.md) object.

**Access**

```
sectionApi.profiles()[*name*]
```

### 57.5.1 GeneralizedProfile(...)

This method creates a GeneralizedProfile object.

**Path**

```
sectionApi.GeneralizedProfile
```

**Prototype**

```
odb_GeneralizedProfile&
GeneralizedProfile(const odb_String& name,
                   double area,
                   double i11,
                   double i12,
                   double i22,
                   double j,
                   double gammaO,
                   double gammaW);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*area*

A Double specifying the cross-sectional area for the profile.

*i11*

A Double specifying the moment of inertia for bending about the 1-axis, ![](../graphics/ker_eqn00019.gif).

*i12*

A Double specifying the moment of inertia for cross bending, ![](../graphics/ker_eqn00020.gif).

*i22*

A Double specifying the moment of inertia for bending about the 2-axis, ![](../graphics/ker_eqn00021.gif).

*j*

A Double specifying the torsional constant, ![](../graphics/ker_eqn00022.gif).

*gammaO*

A Double specifying the sectorial moment, ![](../graphics/ker_eqn00023.gif).

*gammaW*

A Double specifying the warping constant, ![](../graphics/ker_eqn00024.gif).

**Optional arguments**

None.

**Return value**

A GeneralizedProfile object.

**Exceptions**

RangeError.

### 57.5.2 Members

The GeneralizedProfile object has members with the same names and descriptions as the arguments to the [GeneralizedProfile](pt02ch57pyo05.md#ker-generalizedprofile-generalizedprofile-cpp) method.

### 57.5.3 Corresponding analysis keywords

| [*BEAM GENERAL SECTION](../key/key-link.md#usb-kws-mbeamgensect), SECTION=GENERAL or NONLINEAR GENERAL |
| --- |




