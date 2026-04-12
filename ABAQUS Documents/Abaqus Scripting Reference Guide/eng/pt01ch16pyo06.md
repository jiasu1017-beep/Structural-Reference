# 16.6 LeafFromDisplayGroup object







The LeafFromDisplayGroup object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromDisplayGroup object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
import displayGroupOdbToolset
```

### 16.6.1 LeafFromDisplayGroup(...)

This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of Display Group objects.

**Path**

```
LeafFromDisplayGroup
```

**Required argument**

*displayGroup*

A [DisplayGroupArray](pt01ch16pyo01.md) object.

**Optional arguments**

None.

**Return value**

A LeafFromDisplayGroup object.

**Exceptions**

None.

### 16.6.2 Members

The LeafFromDisplayGroup object has members with the same names and descriptions as the arguments to the [LeafFromDisplayGroup](pt01ch16pyo06.md#ker-leaffromdisplaygroup-leaffromdisplaygroup-pyc) method.

In addition, the LeafFromDisplayGroup object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




