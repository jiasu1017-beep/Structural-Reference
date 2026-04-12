# 60.87 Regularization object







The Regularization object defines the tolerance to be used for regularizing material data.

**Access**

```
materialApi.materials()[*name*].regularization()
```

### 60.87.1 Regularization(...)

This method creates a Regularization object.

**Path**

```
materialApi.materials()[*name*].Regularization
```

**Prototype**

```
odb_Regularization&
Regularization(double rtol,
               const odb_String& strainRateRegularization);
```

**Required arguments**

None.

**Optional arguments**

*rtol*

A Double specifying the tolerance to be used for regularizing material data. The default value is 0.03.

*strainRateRegularization*

An odb_String specifying the form of regularization of strain-rate-dependent material data. Possible values are "LOGARITHMIC" and "LINEAR". The default value is "LOGARITHMIC".

**Return value**

A Regularization object.

**Exceptions**

RangeError.

### 60.87.2 Members

The Regularization object has members with the same names and descriptions as the arguments to the [Regularization](pt02ch60pyo87.md#ker-regularization-regularization-cpp) method.

### 60.87.3 Corresponding analysis keywords

| [*DASHPOT](../key/key-link.md#usb-kws-mdashpot) |
| --- |




