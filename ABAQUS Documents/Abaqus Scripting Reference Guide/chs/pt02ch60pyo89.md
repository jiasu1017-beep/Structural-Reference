# 60.89 ShearRetention object







The ShearRetention object defines the reduction of the shear modulus associated with crack surfaces in a [Concrete](pt02ch60pyo18.md) model as a function of the tensile strain across the crack.

**Access**

```
materialApi.materials()[*name*].concrete().shearRetention()
```

### 60.89.1 ShearRetention(...)

This method creates a ShearRetention object.

**Path**

```
materialApi.materials()[*name*].concrete().ShearRetention
```

**Prototype**

```
odb_ShearRetention&
ShearRetention(const odb_SequenceSequenceDouble& table,
               bool temperatureDependency,
               int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- ![](../graphics/ker_eqn00363.gif) for dry concrete. The default value is 1.0.
- ![](../graphics/ker_eqn00364.gif) for dry concrete. The default value is a very large number (full shear retention).
- ![](../graphics/ker_eqn00363.gif) for wet concrete. The default value is 1.0.
- ![](../graphics/ker_eqn00364.gif) for wet concrete. The default value is a very large number (full shear retention).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ShearRetention object.

**Exceptions**

RangeError.

### 60.89.2 Members

The ShearRetention object has members with the same names and descriptions as the arguments to the [ShearRetention](pt02ch60pyo89.md#ker-shearretention-shearretention-cpp) method.

### 60.89.3 Corresponding analysis keywords

| [*SHEAR RETENTION](../key/key-link.md#usb-kws-mshearretention) |
| --- |




