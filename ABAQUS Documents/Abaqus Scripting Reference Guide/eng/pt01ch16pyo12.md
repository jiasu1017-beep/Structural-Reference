# 16.12 LeafFromInstanceElementLabels object







The LeafFromInstanceElementLabels object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromInstanceElementLabels object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
```

### 16.12.1 LeafFromInstanceElementLabels(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of Strings specifying the element labels. Leaf objects specify the items in a display group.

**Path**

```
LeafFromInstanceElementLabels
```

**Required argument**

*elementLabels*

A sequence of sequences specifying element labels. Each inner sequence consists of a [PartInstance](pt01ch06pyo04.md) object followed by a sequence of Strings specifying element labels.

**Optional arguments**

None.

**Return value**

A LeafFromInstanceElementLabels object.

**Exceptions**

None.

### 16.12.2 Members

The LeafFromInstanceElementLabels object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




