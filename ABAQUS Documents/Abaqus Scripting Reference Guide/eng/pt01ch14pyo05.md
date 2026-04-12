# 14.5 RegisteredTuple object







This class allows you to create a tuple that can be queried from the GUI and is capable of notifying the GUI when the contents of any of the tuple's members change.

The RegisteredTuple object is derived from the [CommandRegister](pt01ch14pyo01.md) object.

**Access**

```
import customKernel
```

### 14.5.1 RegisteredTuple(...)

This method creates a RegisteredTuple object.

**Path**

```
customKernel.RegisteredTuple
```

**Required argument**

*tuple*

A tuple of objects. These objects must be derived from the CommandRegister class.

**Optional arguments**

None.

**Return value**

A RegisteredTuple object.

**Exceptions**

None.

### 14.5.2 Methods()

The RegisteredTuple object supports the same methods as a standard Python list object.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 14.5.3 Members

The RegisteredTuple object has no members.




