# 16.22 LeafFromOdbElementLayups object







The LeafFromOdbElementLayups object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromOdbElementLayups object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.22.1 LeafFromOdbElementLayups(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of Strings specifying layup names. Leaf objects specify the items in a display group.

**Path**

```
LeafFromOdbElementLayups
```

**Required argument**

*elementLayups*

A sequence of Strings specifying element layups.

**Optional arguments**

None.

**Return value**

A LeafFromOdbElementLayups object.

**Exceptions**

None.

### 16.22.2 Members

The LeafFromOdbElementLayups object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




