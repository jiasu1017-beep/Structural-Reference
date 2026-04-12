# 60.95 SpecificHeat object







The SpecificHeat object specifies a material's specific heat.

**Access**

```
materialApi.materials()[*name*].specificHeat()
```

### 60.95.1 SpecificHeat(...)

This method creates a SpecificHeat object.

**Path**

```
materialApi.materials()[*name*].SpecificHeat
```

**Prototype**

```
odb_SpecificHeat&
SpecificHeat(const odb_SequenceSequenceDouble& table,
             const odb_String& law,
             bool temperatureDependency,
             int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*law*

An odb_String specifying the specific heat behavior. Possible values are "CONSTANTVOLUME" and "CONSTANTPRESSURE". The default value is "CONSTANTVOLUME".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Specific heat per unit mass.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A SpecificHeat object.

**Exceptions**

RangeError.

### 60.95.2 Members

The SpecificHeat object has members with the same names and descriptions as the arguments to the [SpecificHeat](pt02ch60pyo95.md#ker-specificheat-specificheat-cpp) method.

### 60.95.3 Corresponding analysis keywords

| [*SPECIFIC HEAT](../key/key-link.md#usb-kws-mspecificheat) |
| --- |




