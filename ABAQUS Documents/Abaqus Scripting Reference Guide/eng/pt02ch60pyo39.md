# 60.39 DetonationPoint object







A DetonationPoint object specifies a suboption of the Eos object. The DetonationPoint object defines either isotropic linear elastic shear or linear viscous shear behavior for a hydrodynamic material.

**Access**

```
materialApi.materials()[*name*].eos().detonationPoint()
```

### 60.39.1 DetonationPoint(...)

This method creates a DetonationPoint object.

**Path**

```
materialApi.materials()[*name*].eos().DetonationPoint
```

**Prototype**

```
odb_DetonationPoint&
DetonationPoint(const odb_SequenceSequenceDouble& table);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

None.

**Table data**

- X value for coordinate of detonation point.
- Y value for coordinate of detonation point.
- Z value for coordinate of detonation point.
- Detonation delay time.

**Return value**

A DetonationPoint object.

**Exceptions**

None.

### 60.39.2 Members

The DetonationPoint object has members with the same names and descriptions as the arguments to the [DetonationPoint](pt02ch60pyo39.md#ker-detonationpoint-detonationpoint-cpp) method.

### 60.39.3 Corresponding analysis keywords

| [*DETONATION POINT](../key/key-link.md#usb-kws-mdetonationpt) |
| --- |




