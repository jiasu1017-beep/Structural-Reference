# 16.9 LeafFromElementVarRange object







The LeafFromElementVarRange object can be used whenever a Leaf object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands.

The LeafFromElementVarRange object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.9.1 LeafFromElementVarRange(...)

This method creates a [Leaf](pt01ch16pyo04.md) object from elements with values lying in a variable range. 

**Path**

```
LeafFromElementVarRange
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

A LeafFromElementVarRange object.

**Exceptions**

None.

### 16.9.2 Members

The LeafFromElementVarRange object has members with the same names and descriptions as the arguments to the [LeafFromElementVarRange](pt01ch16pyo09.md#ker-leaffromelementvarrange-leaffromelementvarrange-pyc) method.

In addition, the LeafFromElementVarRange object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




