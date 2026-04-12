# 16.33 LeafFromSets object







The LeafFromSets object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromSets object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
```

### 16.33.1 LeafFromSets(...)

This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of Set objects.

**Path**

```
LeafFromSets
```

**Required argument**

*sets*

A sequence of Set objects.

**Optional arguments**

None.

**Return value**

A LeafFromSets object.

**Exceptions**

None.

### 16.33.2 Members

The LeafFromSets object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




