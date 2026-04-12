# 60.51 FailStress object







The FailStress object defines parameters for stress-based failure measures.

**Access**

```
materialApi.materials()[*name*].elastic().failStress()
```

### 60.51.1 FailStress(...)

This method creates a FailStress object.

**Path**

```
materialApi.materials()[*name*].elastic().FailStress
```

**Prototype**

```
odb_FailStress&
FailStress(const odb_SequenceSequenceDouble& table,
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

- Tensile stress limit in fiber direction, ![](../graphics/ker_eqn00251.gif).
- Compressive stress limit in fiber direction, ![](../graphics/ker_eqn00252.gif).
- Tensile stress limit in transverse direction, ![](../graphics/ker_eqn00253.gif).
- Compressive stress limit in transverse direction, ![](../graphics/ker_eqn00254.gif).
- Shear strength in the ![](../graphics/ker_eqn00083.gif)--![](../graphics/ker_eqn00084.gif) plane, ![](../graphics/ker_eqn00255.gif).
- Cross product term coefficient, ![](../graphics/ker_eqn00256.gif) (![](../graphics/ker_eqn00257.gif)). The default value is zero.
- Biaxial stress limit, ![](../graphics/ker_eqn00258.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A FailStress object.

**Exceptions**

RangeError.

### 60.51.2 Members

The FailStress object has members with the same names and descriptions as the arguments to the [FailStress](pt02ch60pyo51.md#ker-failstress-failstress-cpp) method.

### 60.51.3 Corresponding analysis keywords

| [*FAIL STRESS](../key/key-link.md#usb-kws-mefailstress) |
| --- |




