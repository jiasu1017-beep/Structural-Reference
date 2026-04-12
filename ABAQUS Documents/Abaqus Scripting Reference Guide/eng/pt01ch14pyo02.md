# 14.2 RepositorySupport object







The `RepositorySupport`                 is a base class from which you can derive your own classes that are designed to contain custom repositories. Instances of this class can be queried from the GUI and are capable of notifying the GUI when the contents of the instance change.

The RepositorySupport object is derived from the [CommandRegister](pt01ch14pyo01.md) object.

**Access**

```
import customKernel
mdb.customData
session.customData
session.odbs[*name*].customData
```

### 14.2.1 RepositorySupport()

This method creates a RepositorySupport object.

**Path**

```
customKernel.RepositorySupport
```

**Return value**

A RepositorySupport object.

**Exceptions**

None.

### 14.2.2 Repository(...)

This method installs a repository on the class. The repository is an instance of a `RegisteredDictionary`                       class. Refer to [RegisteredDictionary](pt01ch14pyo03.md)                       for details on its methods.

The objects stored in the repository are assumed to have an attribute called *name*                       that stores the key used to access the object in the repository. The name attribute will be modified by the `changeKey`                       method.

**Required arguments**

*name*

A String specifying the name of the repository.

*constructors*

A constructor or sequence of constructors specifying which classes will store their instances in the repository.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 14.2.3 Members

The RepositorySupport object has no members.




