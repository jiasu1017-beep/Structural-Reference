# 16.14 LeafFromMeshElementLabels object







The LeafFromMeshElementLabels object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromMeshElementLabels object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
```

### 16.14.1 LeafFromMeshElementLabels(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of mesh element objects. Leaf objects specify the items in a display group.

**Path**

```
LeafFromMeshElementLabels
```

**Required argument**

*elementSeq*

A sequence of [MeshElement](pt01ch31pyo05.md) objects specifying elements.

**Optional arguments**

None.

**Return value**

A LeafFromMeshElementLabels object.

**Exceptions**

None.

### 16.14.2 Members

The LeafFromMeshElementLabels object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




