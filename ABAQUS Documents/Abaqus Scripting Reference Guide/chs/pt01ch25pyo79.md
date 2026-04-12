# 25.79 XFEMCrackGrowth object







The XFEMCrackGrowth object defines the enrichment activation state for an [XFEMCrack](pt01ch19pyo16.md).

The XFEMCrackGrowth object is derived from the [Interaction](pt01ch25pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*]
```

### 25.79.1 XFEMCrackGrowth(...)

This method creates an XFEMCrackGrowth object.

**Path**

```
mdb.models[*name*].XFEMCrackGrowth
```

**Required arguments**

*name*

A String specifying the repository key.

*createStepName*

A String specifying the name of the step in which the XFEMCrackGrowth object is created.

*crackName*

A String specifying the [XFEMCrack](pt01ch19pyo16.md) object associated with this interaction.

**Optional argument**

*allowGrowth*

A Boolean specifying whether the crack is allowed to grow (propagate) during this analysis step. The default value is ON.

**Return value**

A XFEMCrackGrowth object.

**Exceptions**

None.

### 25.79.2 setValues(...)

This method modifies the data for an existing XFEMCrackGrowth object in the step where it is created.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [XFEMCrackGrowth](pt01ch25pyo79.md#ker-xfemcrackgrowth-xfemcrackgrowth-pyc) method, except for the *name* and *createStepName* arguments.

**Return value**

None

**Exceptions**

None.

### 25.79.3 setValuesInStep(...)

This method modifies the propagating data for an existing XFEMCrackGrowth object in the specified step.

**Required argument**

*stepName*

A String specifying the name of the step in which the interaction is modified.

**Optional argument**

*allowGrowth*

A Boolean specifying whether the crack is allowed to grow (propagate) during this analysis step. The default value is ON.

**Return value**

None

**Exceptions**

None.

### 25.79.4 Members

The XFEMCrackGrowth object has members with the same names and descriptions as the arguments to the [XFEMCrackGrowth](pt01ch25pyo79.md#ker-xfemcrackgrowth-xfemcrackgrowth-pyc) method.

### 25.79.5 Corresponding analysis keywords

| [*ENRICHMENT ACTIVATION](../key/key-link.md#usb-kws-henrichmentactivation) |
| --- |




