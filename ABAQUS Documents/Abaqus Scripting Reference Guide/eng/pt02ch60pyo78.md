# 60.78 PoreFluidExpansion object







The PoreFluidExpansion object specifies the thermal expansion coefficient for a hydraulic fluid.

**Access**

```
materialApi.materials()[*name*].poreFluidExpansion()
```

### 60.78.1 PoreFluidExpansion(...)

This method creates a PoreFluidExpansion object.

**Path**

```
materialApi.materials()[*name*].PoreFluidExpansion
```

**Prototype**

```
odb_PoreFluidExpansion&
PoreFluidExpansion(const odb_SequenceSequenceDouble& table,
                   double zero,
                   bool temperatureDependency,
                   int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*zero*

A Double specifying the value of ![](../graphics/ker_eqn00061.gif). The default value is 0.0.

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Mean coefficient of thermal expansion, ![](../graphics/ker_eqn00239.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A PoreFluidExpansion object.

**Exceptions**

RangeError.

### 60.78.2 Members

The PoreFluidExpansion object has members with the same names and descriptions as the arguments to the [PoreFluidExpansion](pt02ch60pyo78.md#ker-porefluidexpansion-porefluidexpansion-cpp) method.

### 60.78.3 Corresponding analysis keywords

| [*EXPANSION](../key/key-link.md#usb-kws-mexpansion) |
| --- |




