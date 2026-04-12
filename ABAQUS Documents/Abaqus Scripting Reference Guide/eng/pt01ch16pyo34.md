# 16.34 LeafFromSurfaceSets object







The LeafFromSurfaceSets object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromSurfaceSets object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.34.1 LeafFromSurfaceSets(...)

This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of surface sets.

**Path**

```
LeafFromSurfaceSets
```

**Required argument**

*surfaceSets*

A sequence of Strings specifying surface sets, or a String specifying a single surface set.

**Optional arguments**

None.

**Return value**

A LeafFromSurfaceSets object.

**Exceptions**

None.

### 16.34.2 Members

The LeafFromSurfaceSets object has members with the same names and descriptions as the arguments to the [LeafFromSurfaceSets](pt01ch16pyo34.md#ker-leaffromsurfacesets-leaffromsurfacesets-pyc) method.

In addition, the LeafFromSurfaceSets object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




