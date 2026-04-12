# 60.79 PorousBulkModuli object







The PorousBulkModuli object defines bulk moduli for soils and rocks.

**Access**

```
materialApi.materials()[*name*].porousBulkModuli()
```

### 60.79.1 PorousBulkModuli(...)

This method creates a PorousBulkModuli object.

**Path**

```
materialApi.materials()[*name*].PorousBulkModuli
```

**Prototype**

```
odb_PorousBulkModuli&
PorousBulkModuli(const odb_SequenceSequenceDouble& table,
                 bool temperatureDependency);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional argument**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

**Table data**

- Bulk modulus of solid grains.
- Bulk modulus of permeating fluid.
- Temperature, if the data depend on temperature.

**Return value**

A PorousBulkModuli object.

**Exceptions**

None.

### 60.79.2 Members

The PorousBulkModuli object has members with the same names and descriptions as the arguments to the [PorousBulkModuli](pt02ch60pyo79.md#ker-porousbulkmoduli-porousbulkmoduli-cpp) method.

### 60.79.3 Corresponding analysis keywords

| [*POROUS BULK MODULI](../key/key-link.md#usb-kws-mporousbulkmod) |
| --- |




