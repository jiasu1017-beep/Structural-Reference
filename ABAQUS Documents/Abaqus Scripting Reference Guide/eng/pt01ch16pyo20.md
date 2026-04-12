# 16.20 LeafFromNodeSets object







The LeafFromNodeSets object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromNodeSets object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.20.1 LeafFromNodeSets(...)

This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of node sets.

**Path**

```
LeafFromNodeSets
```

**Required argument**

*nodeSets*

A sequence of Strings specifying node sets or a String specifying a single node set.

**Optional arguments**

None.

**Return value**

A LeafFromNodeSets object.

**Exceptions**

None.

### 16.20.2 Members

The LeafFromNodeSets object has members with the same names and descriptions as the arguments to the [LeafFromNodeSets](pt01ch16pyo20.md#ker-leaffromnodesets-leaffromnodesets-pyc) method.

In addition, the LeafFromNodeSets object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




