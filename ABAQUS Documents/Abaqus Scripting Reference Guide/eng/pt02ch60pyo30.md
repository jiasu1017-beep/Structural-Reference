# 60.30 CyclicHardening object







The CyclicHardening object defines the evolution of the elastic domain for the nonlinear isotropic/kinematic hardening model.

**Access**

```
materialApi.materials()[*name*].plastic().cyclicHardening()
```

### 60.30.1 CyclicHardening(...)

This method creates a CyclicHardening object.

**Path**

```
materialApi.materials()[*name*].plastic().CyclicHardening
```

**Prototype**

```
odb_CyclicHardening&
CyclicHardening(const odb_SequenceSequenceDouble& table,
                bool temperatureDependency,
                int dependencies,
                bool parameters);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*parameters*

A Boolean specifying whether material parameters are to be input directly. The default value is false.

**Table data**

- Equivalent stress.
- ![](../graphics/ker_eqn00160.gif) (only if *parameters*=ON).
- Hardening parameter (only if *parameters*=ON).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CyclicHardening object.

**Exceptions**

None.

### 60.30.2 Members

The CyclicHardening object has members with the same names and descriptions as the arguments to the [CyclicHardening](pt02ch60pyo30.md#ker-cyclichardening-cyclichardening-cpp) method.

### 60.30.3 Corresponding analysis keywords

| [*CYCLIC HARDENING](../key/key-link.md#usb-kws-mcyclichardening) |
| --- |




