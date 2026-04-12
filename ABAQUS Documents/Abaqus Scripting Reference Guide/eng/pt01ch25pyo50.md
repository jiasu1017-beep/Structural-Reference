# 25.50 MasterSlaveAssignment object







The MasterSlaveAssignment object stores the master-slave assignment definition for surfaces in [ContactExp](pt01ch25pyo19.md) and [ContactStd](pt01ch25pyo24.md) objects. The MasterSlaveAssignment object has no constructor or members.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*].masterSlaveAssignments
```

### 25.50.1 changeValuesInStep(...)

This method allows modification of master-slave assignments already defined on surface pairs in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which the master-slave assignments are to be modified.

*index*

An Int specifying the position of the master-slave assignment whose value is to be modified.

*value*

A SymbolicConstant specifying the value of the master-slave role to be assigned to the surface whose index is referenced. Possible values are MASTER, SLAVE, and BALANCED. The SymbolicConstant BALANCED can be specified only in an Abaqus/Standard analysis.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.50.2 appendInStep(...)

This method allows addition of master-slave assignments to new surface pairs in a given step.

**Required arguments**

*stepName*

A String specifying the name of the step in which the master-slave assignments are to be defined.

*assignments*

A sequence of tuples specifying the master-slave assignments. Each tuple contains two entries:
- A region object or the SymbolicConstant GLOBAL specifying the surface to which the master-slave attribute is assigned.
- A SymbolicConstant specifying the overriding master-slave value to be used for the first surface. Possible values of the SymbolicConstant are MASTER, SLAVE, and BALANCED. The SymbolicConstant BALANCED can be specified only in an Abaqus/Standard analysis.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.50.3 delete(...)

The `delete` method allows you to delete existing master-slave assignments.

**Required argument**

*indices*

A sequence of Ints specifying the index of each master-slave assignment to delete.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 25.50.4 Members

The MasterSlaveAssignment object has no members.

### 25.50.5 Corresponding analysis keywords

| [*CONTACT FORMULATION](../key/key-link.md#usb-kws-hcontformulation), TYPE=PURE MASTER-SLAVE |
| --- |
| [*CONTACT FORMULATION](../key/key-link.md#usb-kws-hcontformulation), TYPE=MASTER SLAVE ROLES |




