# 16.32 LeafFromReferencePoint object







The LeafFromReferencePoint object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromReferencePoint object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
```

### 16.32.1 LeafFromReferencePoint(...)

This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of ReferencePoint objects.

**Path**

```
LeafFromReferencePoint
```

**Required argument**

*refPtSeq*

A sequence of Reference Point objects.

**Optional arguments**

None.

**Return value**

A LeafFromReferencePoint object.

**Exceptions**

None.

### 16.32.2 Members

The LeafFromReferencePoint object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




