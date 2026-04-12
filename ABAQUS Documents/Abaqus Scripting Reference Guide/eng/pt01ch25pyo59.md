# 25.59 RegionPairs object







The RegionPairs object stores the domain pair definition for [ContactExp](pt01ch25pyo19.md) and [ContactStd](pt01ch25pyo24.md) objects. The RegionPairs object has no constructor or members.

**Access**

```
import interaction
mdb.models[*name*].interactions[*name*].excludedPairs
mdb.models[*name*].interactions[*name*].includedPairs
```

### 25.59.1 setValuesInStep(...)

This method allows addition and removal of domain pairs in a given step.

**Required argument**

*stepName*

A String specifying the name of the step in which the region pair assignments are to be modified.

**Optional arguments**

*useAllstar*

A Boolean specifying whether the contacting surface pair consists of all exterior faces and -- in an Abaqus/Explicit analysis -- analytical rigid surfaces, shell edges, and beam segments in the model.

*addPairs*

A sequence of pairs of region objects or SymbolicConstants that specify the surface pairs to add to the included pairs of the [ContactExp](pt01ch25pyo19.md) or [ContactStd](pt01ch25pyo24.md) object in the given step. Possible values of the SymbolicConstants are GLOBAL and SELF. When used with [ContactExp](pt01ch25pyo19.md) objects, the second parameter of each pair can also be a string that references an Eulerian material surface.

*removePairs*

A sequence of pairs of region objects or SymbolicConstants that specify the surface pairs to remove from the included pairs of the [ContactExp](pt01ch25pyo19.md) or [ContactStd](pt01ch25pyo24.md) object in the given step. Possible values of the SymbolicConstants are GLOBAL and SELF. When used with [ContactExp](pt01ch25pyo19.md) objects, the second parameter of each pair can also be a string that references an Eulerian material surface.

**Return value**

None

**Exceptions**

None.

### 25.59.2 Members

The RegionPairs object has no members.

### 25.59.3 Corresponding analysis keywords

| [*CONTACT INCLUSIONS](../key/key-link.md#usb-kws-hcontactinclusions) |
| --- |
| [*CONTACT EXCLUSIONS](../key/key-link.md#usb-kws-hcontactexclusions) |




