# 16.4 Leaf object







 Leaf objects are used to specify the items in a display group. Leaf objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands. 

Leaf objects have similarities to Set objects; however, Leaf objects are evaluated when the DisplayGroup expression is evaluated, and they can have SymbolicConstant values (which are also evaluated when the DisplayGroup expression is evaluated).

**Access**

```
import displayGroupMdbToolset
import displayGroupOdbToolset
```

### 16.4.1 Leaf(...)

This method creates a Leaf object.

**Path**

```
Leaf
```

**Required argument**

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.

**Optional arguments**

None.

**Return value**

A Leaf object.

**Exceptions**

None.

### 16.4.2 Members

The Leaf object has members with the same names and descriptions as the arguments to the [Leaf](pt01ch16pyo04.md#ker-leaf-leaf-pyc) method.




