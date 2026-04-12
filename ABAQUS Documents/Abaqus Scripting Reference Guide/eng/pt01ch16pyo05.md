# 16.5 LeafFromDatums object







The LeafFromDatums object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromDatums object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
```

### 16.5.1 LeafFromDatums(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of datum objects. Leaf objects specify the items in a display group.

**Path**

```
LeafFromDatums
```

**Required argument**

*datumSeq*

A sequence of datum objects.

**Optional arguments**

None.

**Return value**

A LeafFromDatums object.

**Exceptions**

None.

### 16.5.2 Members

The LeafFromDatums object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




