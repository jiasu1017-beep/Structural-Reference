# 16.13 LeafFromInstanceNodeLabels object







The LeafFromInstanceNodeLabels object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromInstanceNodeLabels object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
```

### 16.13.1 LeafFromInstanceNodeLabels(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of Strings specifying the node labels. Leaf objects specify the items in a display group.

**Path**

```
LeafFromInstanceNodeLabels
```

**Required argument**

*nodeLabels*

A sequence of sequences specifying node labels. Each inner sequence consists of a [PartInstance](pt01ch06pyo04.md) object followed by a sequence of Strings specifying node labels.

**Optional arguments**

None.

**Return value**

A LeafFromInstanceNodeLabels object.

**Exceptions**

None.

### 16.13.2 Members

The LeafFromInstanceNodeLabels object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




