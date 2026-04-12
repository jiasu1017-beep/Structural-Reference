# 25.22 ContactPropertyAssignment object







The ContactPropertyAssignment object stores the contact property assignment definition for domain pairs in [ContactExp](pt01ch25pyo19.md) and [ContactStd](pt01ch25pyo24.md) objects. The ContactPropertyAssignment object has no constructor or members.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*].contactPropertyAssignments
```

### 25.22.1 changeValuesInStep(...)

This method allows modification of contact property assignments to domain pairs already defined in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which the contact property assignments are to be modified.

*index*

An Int specifying the position of the contact property assignment whose value is to be modified.

*value*

A String specifying the value of the contact property to be assigned to the domain pair whose index is referenced.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.22.2 appendInStep(...)

This method allows addition of contact property assignments to new domain pairs in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which new contact property assignments are to be defined.

*assignments*

A sequence of tuples specifying the properties assigned to each surface pair. Each tuple contains three entries:
- A region object or the SymbolicConstant GLOBAL.
- A region object or the SymbolicConstant SELF. When used with [ContactExp](pt01ch25pyo19.md) objects, this parameter can also be a string that references an Eulerian material surface.
- A String specifying a [ContactProperty](pt01ch25pyo21.md) object associated with this pair of regions.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.22.3 delete(...)

The `delete` method allows you to delete existing contact property assignments.

**Required argument**

*indices*

A sequence of Ints specifying the index of each contact property assignment to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.22.4 Members

The ContactPropertyAssignment object has no members.

### 25.22.5 Corresponding analysis keywords

| [*CONTACT PROPERTY ASSIGNMENT](../key/key-link.md#usb-kws-hcontpropassign) |
| --- |




