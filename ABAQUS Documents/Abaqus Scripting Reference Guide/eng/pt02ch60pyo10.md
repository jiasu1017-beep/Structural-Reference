# 60.10 CapHardening object







The CapHardening object specifies Drucker-Prager/Cap plasticity hardening.

**Access**

```
materialApi.materials()[*name*].capPlasticity().capHardening()
```

### 60.10.1 CapHardening(...)

This method creates a CapHardening object.

**Path**

```
materialApi.materials()[*name*].capPlasticity().CapHardening
```

**Prototype**

```
odb_CapHardening&
CapHardening(const odb_SequenceSequenceDouble& table,
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

- Hydrostatic pressure yield stress.
- Absolute value of the corresponding volumetric inelastic strain.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CapHardening object.

**Exceptions**

RangeError.

### 60.10.2 Members

The CapHardening object has members with the same names and descriptions as the arguments to the [CapHardening](pt02ch60pyo10.md#ker-caphardening-caphardening-cpp) method.

### 60.10.3 Corresponding analysis keywords

| [*CAP HARDENING](../key/key-link.md#usb-kws-mcaphardening) |
| --- |




