# 16.11 LeafFromInstance object







The LeafFromInstance object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromInstance object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupMdbToolset
```

### 16.11.1 LeafFromInstance(...)

This method creates a Leaf object from a sequence of part instance objects.

**Path**

```
LeafFromInstance
```

**Required argument**

*instances*

A [PartInstance](pt01ch06pyo04.md) object or a Sequence of [PartInstance](pt01ch06pyo04.md) objects.

**Optional arguments**

None.

**Return value**

A LeafFromInstance object.

**Exceptions**

If an invalid argument is passed to this method:

```
Cannot define empty leaf.
```

### 16.11.2 Members

The LeafFromInstance object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




