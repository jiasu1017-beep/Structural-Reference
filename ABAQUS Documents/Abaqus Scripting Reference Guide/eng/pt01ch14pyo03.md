# 14.3 RegisteredDictionary object







This class allows you to create a dictionary that can be queried from the GUI and is capable of notifying the GUI when the contents of the dictionary change. The keys to a RegisteredDictionary must be either strings or integers.

The RegisteredDictionary object is derived from the [CommandRegister](pt01ch14pyo01.md) object.

**Access**

```
import customKernel
```

### 14.3.1 RegisteredDictionary()

This method creates a RegisteredDictionary object.

**Path**

```
customKernel.RegisteredDictionary
```

**Return value**

A RegisteredDictionary object.

**Exceptions**

None.

### 14.3.2 Methods()

The RegisteredDictionary object supports the same methods as a Python dictionary. In addition, the RegisteredDictionary object supports the `changeKey`                       method.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 14.3.3 changeKey(...)

This method changes the name of a key in the dictionary.

**Required arguments**

*fromName*

A String or an integer specifying the name of the key to be changed.

*toName*

A String or an integer specifying the new name for the key.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 14.3.4 Members

The RegisteredDictionary object has no members.




