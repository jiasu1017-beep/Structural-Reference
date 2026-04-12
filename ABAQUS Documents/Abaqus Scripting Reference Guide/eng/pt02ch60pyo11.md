# 60.11 CapPlasticity object







The CapPlasticity object specifies the modified Drucker-Prager/Cap plasticity model.

**Access**

```
materialApi.materials()[*name*].capPlasticity()
```

### 60.11.1 CapPlasticity(...)

This method creates a CapPlasticity object.

**Path**

```
materialApi.materials()[*name*].CapPlasticity
```

**Prototype**

```
odb_CapPlasticity&
CapPlasticity(const odb_SequenceSequenceDouble& table,
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

- Material cohesion, ![](../graphics/ker_eqn00082.gif), in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) plane (Abaqus/Standard) or in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) plane (Abaqus/Explicit).
- Material angle of friction, ![](../graphics/ker_eqn00095.gif), in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00093.gif) plane (Abaqus/Standard) or in the ![](../graphics/ker_eqn00092.gif)--![](../graphics/ker_eqn00094.gif) plane (Abaqus/Explicit). Give the value in degrees.
- Cap eccentricity parameter, ![](../graphics/ker_eqn00096.gif). Its value must be greater than zero (typically 0.0 ![](../graphics/ker_eqn00097.gif) 1.0).
- Initial cap yield surface position, ![](../graphics/ker_eqn00098.gif).
- Transition surface radius parameter, ![](../graphics/ker_eqn00090.gif). The default value is 0.0 (i.e., no transition surface).
- (Not used in Abaqus/Explicit) ![](../graphics/ker_eqn00099.gif), the ratio of the flow stress in triaxial tension to the flow stress in triaxial compression. Possible values are 0.778 ![](../graphics/ker_eqn00100.gif) 1.0. If the default value of 0.0 is accepted, Abaqus/Standard assumes ![](../graphics/ker_eqn00101.gif) 1.0.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CapPlasticity object.

**Exceptions**

RangeError.

### 60.11.2 Members

The CapPlasticity object has members with the same names and descriptions as the arguments to the [CapPlasticity](pt02ch60pyo11.md#ker-capplasticity-capplasticity-cpp) method.

In addition, the CapPlasticity object can have the following members:

**Prototype**

```
odb_CapCreepCohesion capCreepCohesion() const;
odb_CapCreepConsolidation capCreepConsolidation() const;
odb_CapHardening capHardening() const;
```

*capCreepCohesion*

A [CapCreepCohesion](pt02ch60pyo08.md) object.

*capCreepConsolidation*

A [CapCreepConsolidation](pt02ch60pyo09.md) object.

*capHardening*

A [CapHardening](pt02ch60pyo10.md) object.

### 60.11.3 Corresponding analysis keywords

| [*CAP PLASTICITY](../key/key-link.md#usb-kws-mcapplasticity) |
| --- |




