# 16.10 LeafFromGeometry object







The LeafFromGeometry object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromGeometry object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
```

### 16.10.1 LeafFromGeometry(...)

This method creates a Leaf object from a sequence of edge, face and cell geometry objects. Any combination of edge, face or cell arguments is allowed however the arguments must specify at least one object--it is not permissible to create an empty leaf.

**Path**

```
LeafFromGeometry
```

**Required arguments**

None.

**Optional arguments**

*edgeSeq*

A sequence of geometry edges.

*faceSeq*

A sequence of geometry faces.

*cellSeq*

A sequence of geometry cells.

**Return value**

A LeafFromGeometry object.

**Exceptions**

If at least one of the sequences is not passed to this method:

```
Cannot define empty leaf.
```

### 16.10.2 Members

The LeafFromGeometry object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




