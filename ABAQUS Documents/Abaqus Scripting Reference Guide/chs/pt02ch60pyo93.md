# 60.93 SoretEffect object







The SoretEffect object defines temperature gradient driven mass diffusion.

**Access**

```
materialApi.materials()[*name*].diffusivity().soretEffect()
```

### 60.93.1 SoretEffect(...)

This method creates a SoretEffect object.

**Path**

```
materialApi.materials()[*name*].diffusivity().SoretEffect
```

**Prototype**

```
odb_SoretEffect&
SoretEffect(const odb_SequenceSequenceDouble& table,
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

- Soret effect factor, ![](../graphics/ker_eqn00367.gif).
- Concentration.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A SoretEffect object.

**Exceptions**

RangeError.

### 60.93.2 Members

The SoretEffect object has members with the same names and descriptions as the arguments to the [SoretEffect](pt02ch60pyo93.md#ker-soreteffect-soreteffect-cpp) method.

### 60.93.3 Corresponding analysis keywords

| [*KAPPA](../key/key-link.md#usb-kws-mkappa) |
| --- |




