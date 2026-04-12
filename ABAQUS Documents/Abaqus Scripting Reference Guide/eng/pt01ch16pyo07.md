# 16.7 LeafFromElementLabels object







The LeafFromElementLabels object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromElementLabels object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.7.1 LeafFromElementLabels(...)

This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of element labels that belong to a single part instance.

**Path**

```
LeafFromElementLabels
```

**Required arguments**

*partInstanceName*

A String specifying the name of the part instance to which *elementLabels* refers.

*elementLabels*

A sequence of Strings specifying expressions that denote element labels. The expression can be any of the following:
- An Int specifying a single element label; for example, `1`.
- A String specifying a single element label; for example, `'7'`.
- A String specifying a sequence of element labels; for example, `'3:5'` and `'3:15:3'`.

**Optional arguments**

None.

**Return value**

A LeafFromElementLabels object.

**Exceptions**

None.

### 16.7.2 Members

The LeafFromElementLabels object has members with the same names and descriptions as the arguments to the [LeafFromElementLabels](pt01ch16pyo07.md#ker-leaffromelementlabels-leaffromelementlabels-pyc) method.

In addition, the LeafFromElementLabels object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




