# 29.48 EosCompaction object







The EosCompaction object specifies material eos compaction.

**Access**

```
import material
mdb.models[*name*].materials[*name*].eos.eosCompaction
import odbMaterial
session.odbs[*name*].materials[*name*].eos.eosCompaction
```

### 29.48.1 EosCompaction(...)

This method creates a EosCompaction object.

**Path**

```
mdb.models[*name*].materials[*name*].eos.EosCompaction
session.odbs[*name*].materials[*name*].eos.EosCompaction
```

**Required arguments**

*soundSpeed*

A Float specifying reference sound speed in the porous material.

*porosity*

A Float specifying value of the porosity of the unloaded material.

*pressure*

A Float specifying pressure required to initialize plastic behavior.

*compactionPressure*

A Float specifying compaction pressure at which all pores are crushed.

**Optional arguments**

None.

**Return value**

An EosCompaction object.

**Exceptions**

RangeError.

### 29.48.2 setValues(...)

This method modifies the EosCompaction object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [EosCompaction](pt01ch29pyo48.md#ker-eoscompaction-eoscompaction-pyc) method.

**Return value**

None

**Exceptions**

RangeError.

### 29.48.3 Members

The EosCompaction object has members with the same names and descriptions as the arguments to the [EosCompaction](pt01ch29pyo48.md#ker-eoscompaction-eoscompaction-pyc) method.

### 29.48.4 Corresponding analysis keywords

| [*EOS COMPACTION](../key/key-link.md#usb-kws-meoscompaction) |
| --- |




