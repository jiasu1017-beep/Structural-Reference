# 60.41 Diffusivity object







The Diffusivity object specifies mass diffusivity.

**Access**

```
materialApi.materials()[*name*].diffusivity()
```

### 60.41.1 Diffusivity(...)

This method creates a Diffusivity object.

**Path**

```
materialApi.materials()[*name*].Diffusivity
```

**Prototype**

```
odb_Diffusivity&
Diffusivity(const odb_SequenceSequenceDouble& table,
            const odb_String& type,
            const odb_String& law,
            bool temperatureDependency,
            int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*type*

An odb_String specifying the type of diffusivity. Possible values are "ISOTROPIC", "ORTHOTROPIC", and "ANISOTROPIC". The default value is "ISOTROPIC".

*law*

An odb_String specifying the diffusion behavior. Possible values are "GENERAL" and "FICK". The default value is "GENERAL".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=ISOTROPIC, the table data specify the following:
- Diffusivity, ![](../graphics/ker_eqn00172.gif).
- Concentration, ![](../graphics/ker_eqn00173.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ORTHOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00174.gif).
- ![](../graphics/ker_eqn00031.gif).
- ![](../graphics/ker_eqn00034.gif).
- Concentration, ![](../graphics/ker_eqn00173.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ANISOTROPIC, the table data specify the following:- ![](../graphics/ker_eqn00174.gif).
- ![](../graphics/ker_eqn00175.gif).
- ![](../graphics/ker_eqn00031.gif).
- ![](../graphics/ker_eqn00176.gif).
- ![](../graphics/ker_eqn00032.gif).
- ![](../graphics/ker_eqn00034.gif).
- Concentration, ![](../graphics/ker_eqn00173.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Diffusivity object.

**Exceptions**

RangeError.

### 60.41.2 Members

The Diffusivity object has members with the same names and descriptions as the arguments to the [Diffusivity](pt02ch60pyo41.md#ker-diffusivity-diffusivity-cpp) method.

In addition, the Diffusivity object can have the following members:

**Prototype**

```
odb_PressureEffect pressureEffect() const;
odb_SoretEffect soretEffect() const;
```

*pressureEffect*

A [PressureEffect](pt02ch60pyo84.md) object.

*soretEffect*

A [SoretEffect](pt02ch60pyo93.md) object.

### 60.41.3 Corresponding analysis keywords

| [*DIFFUSIVITY](../key/key-link.md#usb-kws-mdiffusivity) |
| --- |




