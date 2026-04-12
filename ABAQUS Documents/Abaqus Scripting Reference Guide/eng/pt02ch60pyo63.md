# 60.63 Hysteresis object







The Hysteresis object specifies the creep part of the material model for the hysteretic behavior of elastomers.

**Access**

```
materialApi.materials()[*name*].hyperelastic().hysteresis()
```

### 60.63.1 Hysteresis(...)

This method creates a Hysteresis object.

**Path**

```
materialApi.materials()[*name*].hyperelastic().Hysteresis
```

**Prototype**

```
odb_Hysteresis&
Hysteresis(const odb_SequenceSequenceDouble& table);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

None.

**Table data**

- Stress scaling factor.
- Creep parameter.
- Effective stress exponent.
- Creep strain exponent.

**Return value**

A Hysteresis object.

**Exceptions**

RangeError.

### 60.63.2 Members

The Hysteresis object has members with the same names and descriptions as the arguments to the [Hysteresis](pt02ch60pyo63.md#ker-hysteresis-hysteresis-cpp) method.

### 60.63.3 Corresponding analysis keywords

| [*HYSTERESIS](../key/key-link.md#usb-kws-mhysteresis) |
| --- |




