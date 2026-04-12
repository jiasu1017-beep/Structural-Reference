# 16.27 LeafFromOdbElementTypes object







The LeafFromOdbElementTypes object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromOdbElementTypes object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.27.1 LeafFromOdbElementTypes(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of Strings specifying element names. Leaf objects specify the items in a display group.

**Path**

```
LeafFromOdbElementTypes
```

**Required argument**

*elementTypes*

A sequence of Strings specifying element Types.

**Optional arguments**

None.

**Return value**

A LeafFromOdbElementTypes object.

**Exceptions**

None.

### 16.27.2 Members

The LeafFromOdbElementTypes object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




