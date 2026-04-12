# 25.47 InitializationAssignment object







The InitializationAssignment object stores the contact initialization assignment definition for domain pairs in a [ContactStd](pt01ch25pyo24.md) object. The InitializationAssignment object has no constructor or members.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*].initializationAssignments
```

### 25.47.1 changeValuesInStep(...)

This method allows modification of contact initialization assignments to domain pairs already defined in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which the contact initialization assignments are to be modified.

*index*

An Int specifying the position of the contact initialization assignment whose value is to be modified.

*value*

A String specifying the value of the contact initialization to be assigned to the domain pair whose index is referenced.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.47.2 appendInStep(...)

This method allows addition of contact initialization assignments to new domain pairs in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which new contact initialization assignments are to be defined.

*assignments*

A sequence of tuples specifying the initializations assigned to each surface pair. Each tuple contains three entries:
- A region object or the SymbolicConstant GLOBAL.
- A region object or the SymbolicConstant SELF.
- A String specifying a [StdInitialization](pt01ch25pyo67.md) object associated with this pair of regions.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.47.3 delete(...)

The `delete` method allows you to delete existing contact initialization assignments from a [ContactStd](pt01ch25pyo24.md) object.

**Required argument**

*indices*

A sequence of Ints specifying the index of each contact initialization assignment to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.47.4 Members

The InitializationAssignment object has no members.

### 25.47.5 Corresponding analysis keywords

| [*CONTACT INITIALIZATION ASSIGNMENT](../key/key-link.md#usb-kws-hcontinitassign) |
| --- |




