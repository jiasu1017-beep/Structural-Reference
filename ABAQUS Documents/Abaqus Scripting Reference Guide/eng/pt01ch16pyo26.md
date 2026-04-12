# 16.26 LeafFromOdbElementSections object







The LeafFromOdbElementSections object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromOdbElementSections object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.26.1 LeafFromOdbElementSections(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of Strings specifying section names. Leaf objects specify the items in a display group.

**Path**

```
LeafFromOdbElementSections
```

**Required argument**

*elementSections*

A sequence of Strings specifying element Sections.

**Optional arguments**

None.

**Return value**

A LeafFromOdbElementSections object.

**Exceptions**

None.

### 16.26.2 Members

The LeafFromOdbElementSections object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




