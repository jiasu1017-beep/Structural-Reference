# 60.37 Density object







The Density object specifies the material density.

**Access**

```
materialApi.materials()[*name*].density()
```

### 60.37.1 Density(...)

This method creates a Density object.

**Path**

```
materialApi.materials()[*name*].Density
```

**Prototype**

```
odb_Density&
Density(const odb_SequenceSequenceDouble& table,
        bool temperatureDependency,
        int dependencies,
        const odb_String& distributionType,
        const odb_String& fieldName);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*distributionType*

An odb_String specifying how the density is distributed spatially. Possible values are "UNIFORM", "ANALYTICAL_FIELD", and "DISCRETE_FIELD". The default value is "UNIFORM".

*fieldName*

An odb_String specifying the name of the [AnalyticalField](#ker-analyticalfield-cpp) or [DiscreteField](#ker-discretefield-cpp) object associated with this material option. The *fieldName* argument applies only when *distributionType*="ANALYTICAL_FIELD" or *distributionType*="DISCRETE_FIELD". The default value is an empty string.

**Table data**

- The mass density.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Density object.

**Exceptions**

RangeError.

### 60.37.2 Members

The Density object has members with the same names and descriptions as the arguments to the [Density](pt02ch60pyo37.md#ker-density-density-cpp) method.

### 60.37.3 Corresponding analysis keywords

| [*DENSITY](../key/key-link.md#usb-kws-mdensity) |
| --- |




