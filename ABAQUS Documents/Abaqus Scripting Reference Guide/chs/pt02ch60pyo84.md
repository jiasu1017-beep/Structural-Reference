# 60.84 PressureEffect object







The PressureEffect object defines equivalent pressure stress driven mass diffusion.

**Access**

```
materialApi.materials()[*name*].diffusivity().pressureEffect()
```

### 60.84.1 PressureEffect(...)

This method creates a PressureEffect object.

**Path**

```
materialApi.materials()[*name*].diffusivity().PressureEffect
```

**Prototype**

```
odb_PressureEffect&
PressureEffect(const odb_SequenceSequenceDouble& table,
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

- Pressure stress factor, ![](../graphics/ker_eqn00356.gif).
- Concentration.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A PressureEffect object.

**Exceptions**

RangeError.

### 60.84.2 Members

The PressureEffect object has members with the same names and descriptions as the arguments to the [PressureEffect](pt02ch60pyo84.md#ker-pressureeffect-pressureeffect-cpp) method.

### 60.84.3 Corresponding analysis keywords

| [*KAPPA](../key/key-link.md#usb-kws-mkappa) |
| --- |




