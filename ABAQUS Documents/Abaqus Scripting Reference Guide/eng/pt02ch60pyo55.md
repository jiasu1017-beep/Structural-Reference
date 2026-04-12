# 60.55 GasketMembraneElastic object







The GasketMembraneElastic object defines the elastic parameters for the membrane shear behavior of a gasket.

**Access**

```
materialApi.materials()[*name*].gasketMembraneElastic()
```

### 60.55.1 GasketMembraneElastic(...)

This method creates a GasketMembraneElastic object.

**Path**

```
materialApi.materials()[*name*].GasketMembraneElastic
```

**Prototype**

```
odb_GasketMembraneElastic&
GasketMembraneElastic(const odb_SequenceSequenceDouble& table,
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

- Young's modulus, ![](../graphics/ker_eqn00163.gif).
- Poisson's ratio, ![](../graphics/ker_eqn00164.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A GasketMembraneElastic object.

**Exceptions**

RangeError.

### 60.55.2 Members

The GasketMembraneElastic object has members with the same names and descriptions as the arguments to the [GasketMembraneElastic](pt02ch60pyo55.md#ker-gasketmembraneelastic-gasketmembraneelastic-cpp) method.

### 60.55.3 Corresponding analysis keywords

| [*GASKET ELASTICITY](../key/key-link.md#usb-kws-mgasketelastic) |
| --- |




