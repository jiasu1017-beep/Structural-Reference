# 60.80 PorousElastic object







The PorousElastic object specifies elastic material properties for porous materials.

**Access**

```
materialApi.materials()[*name*].porousElastic()
```

### 60.80.1 PorousElastic(...)

This method creates a PorousElastic object.

**Path**

```
materialApi.materials()[*name*].PorousElastic
```

**Prototype**

```
odb_PorousElastic&
PorousElastic(const odb_SequenceSequenceDouble& table,
              const odb_String& shear,
              bool temperatureDependency,
              int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*shear*

An odb_String specifying the shear definition form. Possible values are "G" and "POISSON". The default value is "POISSON".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *shear*=G, the table data specify the following:
- The logarithmic bulk modulus, ![](../graphics/ker_eqn00342.gif). (Dimensionless.)
- The shear modulus, ![](../graphics/ker_eqn00182.gif).
- The elastic tensile limit, ![](../graphics/ker_eqn00343.gif). (This value cannot be negative.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *shear*=POISSON, the table data specify the following:- The logarithmic bulk modulus, ![](../graphics/ker_eqn00342.gif). (Dimensionless.)
- The Poisson's ratio, ![](../graphics/ker_eqn00164.gif).
- The elastic tensile limit, ![](../graphics/ker_eqn00343.gif). (This value cannot be negative.)
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A PorousElastic object.

**Exceptions**

RangeError.

### 60.80.2 Members

The PorousElastic object has members with the same names and descriptions as the arguments to the [PorousElastic](pt02ch60pyo80.md#ker-porouselastic-porouselastic-cpp) method.

### 60.80.3 Corresponding analysis keywords

| [*POROUS ELASTIC](../key/key-link.md#usb-kws-mporouselastic) |
| --- |




