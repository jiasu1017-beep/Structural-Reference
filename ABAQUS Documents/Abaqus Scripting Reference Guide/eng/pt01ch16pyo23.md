# 16.23 LeafFromOdbElementMaterials object







The LeafFromOdbElementMaterials object can be used whenever a [Leaf](pt01ch16pyo04.md) object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromOdbElementMaterials object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.23.1 LeafFromOdbElementMaterials(...)

 This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of Strings specifying material names. Leaf objects specify the items in a display group.

**Path**

```
LeafFromOdbElementMaterials
```

**Required argument**

*elementMaterials*

A sequence of Strings specifying element materials.

**Optional arguments**

None.

**Return value**

A LeafFromOdbElementMaterials object.

**Exceptions**

None.

### 16.23.2 Members

The LeafFromOdbElementMaterials object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




