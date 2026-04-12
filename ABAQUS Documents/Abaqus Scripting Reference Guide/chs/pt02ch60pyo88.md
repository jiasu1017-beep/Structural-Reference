# 60.88 SaturationDependence object







The SaturationDependence object specifies the dependence of the permeability of a material on the saturation of the wetting liquid.

**Access**

```
materialApi.materials()[*name*].permeability().saturationDependence()
```

### 60.88.1 SaturationDependence(...)

This method creates a SaturationDependence object.

**Path**

```
materialApi.materials()[*name*].permeability().SaturationDependence
```

**Prototype**

```
odb_SaturationDependence&
SaturationDependence(const odb_SequenceSequenceDouble& table);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

None.

**Table data**

- ![](../graphics/ker_eqn00362.gif). (Dimensionless.)
- Saturation, ![](../graphics/ker_eqn00234.gif). (Dimensionless.)

**Return value**

A SaturationDependence object.

**Exceptions**

RangeError.

### 60.88.2 Members

The SaturationDependence object has members with the same names and descriptions as the arguments to the [SaturationDependence](pt02ch60pyo88.md#ker-saturationdependence-saturationdependence-cpp) method.

### 60.88.3 Corresponding analysis keywords

| [*PERMEABILITY](../key/key-link.md#usb-kws-mpermeabil) |
| --- |




