# 16.25 LeafFromOdbElementPlies object







The LeafFromOdbElementPlies object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromOdbElementPlies object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.25.1 LeafFromOdbElementPlies(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of Strings specifying ply names. Leaf objects specify the items in a display group.

**Path**

```
LeafFromOdbElementPlies
```

**Required argument**

*elementPlies*

A sequence of Strings specifying element plies.

**Optional arguments**

None.

**Return value**

A LeafFromOdbElementPlies object.

**Exceptions**

None.

### 16.25.2 Members

The LeafFromOdbElementPlies object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




