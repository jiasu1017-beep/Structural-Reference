# 16.21 LeafFromNodeVarRange object







The LeafFromNodeVarRange object can be used whenever a Leaf object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromNodeVarRange object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.21.1 LeafFromNodeVarRange(...)

This method creates a [Leaf](pt01ch16pyo04.md) object from nodes with values lying in a variable range. 

**Path**

```
LeafFromNodeVarRange
```

**Required arguments**

None.

**Optional arguments**

*minimumRange*

A Float specifying the minimum value for the variable range. The default value is 3.40282346639E38.

*maximumRange*

A Float specifying the maximum value for the variable range. The default value is 3.40282346639e+038.

*insideRange*

A Boolean specifying the method used to evaluate the range. If *insideRange*=ON, the range falls inside the specified minimum and maximum values. The default value is ON.

**Return value**

A LeafFromNodeVarRange object.

**Exceptions**

None.

### 16.21.2 Members

The LeafFromNodeVarRange object has members with the same names and descriptions as the arguments to the [LeafFromNodeVarRange](pt01ch16pyo21.md#ker-leaffromnodevarrange-leaffromnodevarrange-pyc) method.

In addition, the LeafFromNodeVarRange object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




