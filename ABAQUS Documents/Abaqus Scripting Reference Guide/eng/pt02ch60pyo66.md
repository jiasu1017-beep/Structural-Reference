# 60.66 LatentHeat object







The LatentHeat object specifies a material's latent heat.

**Access**

```
materialApi.materials()[*name*].latentHeat()
```

### 60.66.1 LatentHeat(...)

This method creates a LatentHeat object.

**Path**

```
materialApi.materials()[*name*].LatentHeat
```

**Prototype**

```
odb_LatentHeat&
LatentHeat(const odb_SequenceSequenceDouble& table);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

None.

**Table data**

- Latent heat per unit mass.
- Solidus temperature.
- Liquidus temperature.

**Return value**

A LatentHeat object.

**Exceptions**

RangeError.

### 60.66.2 Members

The LatentHeat object has members with the same names and descriptions as the arguments to the [LatentHeat](pt02ch60pyo66.md#ker-latentheat-latentheat-cpp) method.

### 60.66.3 Corresponding analysis keywords

| [*LATENT HEAT](../key/key-link.md#usb-kws-mlatentheat) |
| --- |




