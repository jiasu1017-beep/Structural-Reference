# 60.48 EosCompaction object







The EosCompaction object specifies material eos compaction.

**Access**

```
materialApi.materials()[*name*].eos().eosCompaction()
```

### 60.48.1 EosCompaction(...)

This method creates a EosCompaction object.

**Path**

```
materialApi.materials()[*name*].eos().EosCompaction
```

**Prototype**

```
odb_EosCompaction&
EosCompaction(double soundSpeed,
              double porosity,
              double pressure,
              double compactionPressure);
```

**Required arguments**

*soundSpeed*

A Double specifying reference sound speed in the porous material.

*porosity*

A Double specifying value of the porosity of the unloaded material.

*pressure*

A Double specifying pressure required to initialize plastic behavior.

*compactionPressure*

A Double specifying compaction pressure at which all pores are crushed.

**Optional arguments**

None.

**Return value**

An EosCompaction object.

**Exceptions**

RangeError.

### 60.48.2 Members

The EosCompaction object has members with the same names and descriptions as the arguments to the [EosCompaction](pt02ch60pyo48.md#ker-eoscompaction-eoscompaction-cpp) method.

### 60.48.3 Corresponding analysis keywords

| [*EOS COMPACTION](../key/key-link.md#usb-kws-meoscompaction) |
| --- |




