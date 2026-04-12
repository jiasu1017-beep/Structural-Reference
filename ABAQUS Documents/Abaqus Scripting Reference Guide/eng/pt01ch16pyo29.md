# 16.29 LeafFromPartElementLabels object







The LeafFromPartElementLabels object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromPartElementLabels object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
```

### 16.29.1 LeafFromPartElementLabels(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of Strings specifying element labels. Leaf objects specify the items in a display group.

**Path**

```
LeafFromPartElementLabels
```

**Required arguments**

*part*

A [Part](pt01ch37pyo01.md) object.

*elementLabels*

A sequence of Strings specifying element labels.

**Optional arguments**

None.

**Return value**

A LeafFromPartElementLabels object.

**Exceptions**

None.

### 16.29.2 Members

The LeafFromPartElementLabels object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




