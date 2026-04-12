# 60.18 Concrete object







The Concrete object defines concrete properties beyond the elastic range.

**Access**

```
materialApi.materials()[*name*].concrete()
```

### 60.18.1 Concrete(...)

This method creates a Concrete object.

**Path**

```
materialApi.materials()[*name*].Concrete
```

**Prototype**

```
odb_Concrete&
Concrete(const odb_SequenceSequenceDouble& table,
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

- Absolute value of compressive stress.
- Absolute value of plastic strain.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A Concrete object.

**Exceptions**

RangeError.

### 60.18.2 Members

The Concrete object has members with the same names and descriptions as the arguments to the [Concrete](pt02ch60pyo18.md#ker-concrete-concrete-cpp) method.

In addition, the Concrete object can have the following members:

**Prototype**

```
odb_FailureRatios failureRatios() const;
odb_ShearRetention shearRetention() const;
odb_TensionStiffening tensionStiffening() const;
```

*failureRatios*

A [FailureRatios](pt02ch60pyo52.md) object.

*shearRetention*

A [ShearRetention](pt02ch60pyo89.md) object.

*tensionStiffening*

A [TensionStiffening](pt02ch60pyo98.md) object.

### 60.18.3 Corresponding analysis keywords

| [*CONCRETE](../key/key-link.md#usb-kws-mconcrete) |
| --- |




