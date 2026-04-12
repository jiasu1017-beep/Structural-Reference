# 60.82 PorousMetalPlasticity object







The PorousMetalPlasticity object specifies a porous metal plasticity model.

**Access**

```
materialApi.materials()[*name*].porousMetalPlasticity()
```

### 60.82.1 PorousMetalPlasticity(...)

This method creates a PorousMetalPlasticity object.

**Path**

```
materialApi.materials()[*name*].PorousMetalPlasticity
```

**Prototype**

```
odb_PorousMetalPlasticity&
PorousMetalPlasticity(const odb_SequenceSequenceDouble& table,
                      odb_Union relativeDensity,
                      bool temperatureDependency,
                      int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*relativeDensity*

The string "NONE" or a Double specifying the initial relative density of the material, ![](../graphics/ker_eqn00346.gif). The default value is "NONE".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- ![](../graphics/ker_eqn00347.gif).
- ![](../graphics/ker_eqn00348.gif).
- ![](../graphics/ker_eqn00349.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A PorousMetalPlasticity object.

**Exceptions**

RangeError.

### 60.82.2 Members

The PorousMetalPlasticity object has members with the same names and descriptions as the arguments to the [PorousMetalPlasticity](pt02ch60pyo82.md#ker-porousmetalplasticity-porousmetalplasticity-cpp) method.

In addition, the PorousMetalPlasticity object can have the following members:

**Prototype**

```
odb_PorousFailureCriteria porousFailureCriteria() const;
odb_VoidNucleation voidNucleation() const;
```

*porousFailureCriteria*

A [PorousFailureCriteria](pt02ch60pyo81.md) object.

*voidNucleation*

A [VoidNucleation](pt02ch60pyo109.md) object.

### 60.82.3 Corresponding analysis keywords

| [*POROUS METAL PLASTICITY](../key/key-link.md#usb-kws-mpormetalplas) |
| --- |




