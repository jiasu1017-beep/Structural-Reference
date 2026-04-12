# 16.19 LeafFromNodeLabels object







The LeafFromNodeLabels object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromNodeLabels object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.19.1 LeafFromNodeLabels(...)

This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of node labels that belong to a single part instance.

**Path**

```
LeafFromNodeLabels
```

**Required arguments**

*partInstanceName*

A String specifying the name of the part instance to which *nodeLabels* refers.

*nodeLabels*

A sequence of Strings specifying expressions that denote node labels. The expression can be any of the following:
- An Int specifying a single node label; for example, `1`.
- A String specifying a single node label; for example, `'7'`.
- A String specifying a sequence of node labels; for example, `'3:5'` and `'3:15:3'`.

**Optional arguments**

None.

**Return value**

A LeafFromNodeLabels object.

**Exceptions**

None.

### 16.19.2 Members

The LeafFromNodeLabels object has members with the same names and descriptions as the arguments to the [LeafFromNodeLabels](pt01ch16pyo19.md#ker-leaffromnodelabels-leaffromnodelabels-pyc) method.

In addition, the LeafFromNodeLabels object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




