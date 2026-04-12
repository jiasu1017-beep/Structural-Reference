# 16.28 LeafFromOdbNodePick object







The LeafFromOdbNodePick object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromOdbNodePick object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.28.1 LeafFromOdbNodePick(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a tuple containing machine readable, compact strings defining the nodes picked for each part instance. Leaf objects specify the items in a display group.

**Path**

```
LeafFromOdbNodePick
```

**Required argument**

*nodePick*

A sequence of tuples of the form [part name, entity count, machine readable pick strings].

**Optional arguments**

None.

**Return value**

A LeafFromOdbNodePick object.

**Exceptions**

None.

### 16.28.2 Members

The LeafFromOdbNodePick object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




