# 25.65 StabilizationAssignment object







The StabilizationAssignment object stores the contact stabilization assignment definition for domain pairs in a [ContactStd](pt01ch25pyo24.md) object. The StabilizationAssignment object has no constructor or members.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*].stabilizationAssignments
```

### 25.65.1 changeValuesInStep(...)

This method allows modification of contact stabilization assignments to domain pairs already defined in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which the contact stabilization assignments are to be modified.

*index*

An Int specifying the position of the contact stabilization assignment whose value is to be modified.

*value*

A String specifying the value of the contact stabilization to be assigned to the domain pair whose index is referenced.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.65.2 appendInStep(...)

This method allows addition of contact stabilization assignments to new domain pairs in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which new contact stabilization assignments are to be defined.

*assignments*

A sequence of tuples specifying the stabilizations assigned to each surface pair. Each tuple contains three entries:
- A region object or the SymbolicConstant GLOBAL.
- A region object or the SymbolicConstant SELF.
- A String specifying a [StdStabilization](pt01ch25pyo68.md) object associated with this pair of regions.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.65.3 delete(...)

The `delete` method allows you to delete existing contact stabilization assignments from a [ContactStd](pt01ch25pyo24.md) object.

**Required argument**

*indices*

A sequence of Ints specifying the index of each contact stabilization assignment to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.65.4 Members

The StabilizationAssignment object has no members.

### 25.65.5 Corresponding analysis keywords

| [*CONTACT STABILIZATION](../key/key-link.md#usb-kws-hcontactstab) |
| --- |




