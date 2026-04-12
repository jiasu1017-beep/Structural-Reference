# 60.96 Swelling object







The Swelling object specifies time-dependent volumetric swelling for a material.

**Access**

```
materialApi.materials()[*name*].swelling()
```

### 60.96.1 Swelling(...)

This method creates a Swelling object.

**Path**

```
materialApi.materials()[*name*].Swelling
```

**Prototype**

```
odb_Swelling&
Swelling(const odb_SequenceSequenceDouble& table,
         const odb_String& law,
         bool temperatureDependency,
         int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

This argument is valid only when *law*="INPUT".

**Optional arguments**

*law*

An odb_String specifying the type of data defining the swelling behavior. Possible values are "INPUT" and "USER". The default value is "INPUT".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

- Volumetric swelling strain rate.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Swelling object.

**Exceptions**

RangeError.

### 60.96.2 Members

The Swelling object has members with the same names and descriptions as the arguments to the [Swelling](pt02ch60pyo96.md#ker-swelling-swelling-cpp) method.

In addition, the Swelling object can have the following member:

**Prototype**

```
odb_Ratios ratios() const;
```

*ratios*

A [Ratios](pt02ch60pyo86.md) object.

### 60.96.3 Corresponding analysis keywords

| [*SWELLING](../key/key-link.md#usb-kws-mswelling) |
| --- |




