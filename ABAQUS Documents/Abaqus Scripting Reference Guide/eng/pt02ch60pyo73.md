# 60.73 Ornl object







The Ornl object specifies the constitutive model developed by Oak Ridge National Laboratory.

**Access**

```
materialApi.materials()[*name*].creep().ornl()
materialApi.materials()[*name*].plastic().ornl()
```

### 60.73.1 Ornl(...)

This method creates an Ornl object.

**Path**

```
materialApi.materials()[*name*].creep().Ornl
materialApi.materials()[*name*].plastic().Ornl
```

**Prototype**

```
odb_Ornl&
Ornl(double a,
     odb_Union h,
     bool reset);
```

**Required arguments**

None.

**Optional arguments**

*a*

A Double specifying the saturation rates for kinematic shift caused by creep strain, as defined by Equation (15) of Section 4.3.3–3 of the Nuclear Standard. The default value corresponds to that section of the Standard. Set *a*=0.0 to use the 1986 revision of the Standard. The default value is 0.3.

*h*

The string "NONE" or a Double specifying the rate of kinematic shift with respect to creep strain [Equation (7) of Section 4.3.2–1 of the Nuclear Standard]. If *h*="NONE", the value of *h* is determined according to Section 4.3.3–3 of the 1981 revision of the Standard. Set *h*=0.0 to use the 1986 revision of the Standard. The default value is "NONE".

*reset*

A Boolean specifying whether to invoke the optional ![](../graphics/ker_eqn00090.gif) reset procedure described in Section 4.3.5 of the Nuclear Standard. The default value is false.

**Return value**

An Ornl object.

**Exceptions**

RangeError.

### 60.73.2 Members

The Ornl object has members with the same names and descriptions as the arguments to the [Ornl](pt02ch60pyo73.md#ker-ornl-ornl-cpp) method.

### 60.73.3 Corresponding analysis keywords

| [*ORNL](../key/key-link.md#usb-kws-mornl) |
| --- |




