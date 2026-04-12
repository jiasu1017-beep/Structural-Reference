# 60.36 DeformationPlasticity object







The DeformationPlasticity object specifies the deformation plasticity model.

**Access**

```
materialApi.materials()[*name*].deformationPlasticity()
```

### 60.36.1 DeformationPlasticity(...)

This method creates a DeformationPlasticity object.

**Path**

```
materialApi.materials()[*name*].DeformationPlasticity
```

**Prototype**

```
odb_DeformationPlasticity&
DeformationPlasticity(const odb_SequenceSequenceDouble& table,
                      bool temperatureDependency);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional argument**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

**Table data**

- Young's modulus, ![](../graphics/ker_eqn00163.gif).
- Poisson's ratio, ![](../graphics/ker_eqn00164.gif).
- Yield stress, ![](../graphics/ker_eqn00165.gif).
- Exponent, ![](../graphics/ker_eqn00088.gif).
- Yield offset, ![](../graphics/ker_eqn00090.gif).
- Temperature, if the data depend on temperature.

**Return value**

A DeformationPlasticity object.

**Exceptions**

RangeError.

### 60.36.2 Members

The DeformationPlasticity object has members with the same names and descriptions as the arguments to the [DeformationPlasticity](pt02ch60pyo36.md#ker-deformationplasticity-deformationplasticity-cpp) method.

### 60.36.3 Corresponding analysis keywords

| [*DEFORMATION PLASTICITY](../key/key-link.md#usb-kws-mdeformplas) |
| --- |




