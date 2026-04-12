# 16.15 LeafFromMeshNodeLabels object







The LeafFromMeshNodeLabels object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromMeshNodeLabels object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
```

### 16.15.1 LeafFromMeshNodeLabels(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of mesh node objects. Leaf objects specify the items in a display group.

**Path**

```
LeafFromMeshNodeLabels
```

**Required argument**

*nodeSeq*

A sequence of [MeshNode](pt01ch31pyo09.md) objects specifying nodes.

**Optional arguments**

None.

**Return value**

A LeafFromMeshNodeLabels object.

**Exceptions**

None.

### 16.15.2 Members

The LeafFromMeshNodeLabels object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




