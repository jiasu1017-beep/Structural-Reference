# 16.17 LeafFromModelElemLabels object







The LeafFromModelElemLabels object can be used whenever a Leaf object is expected as an argument. [Leaf](pt01ch16pyo04.md) objects are used to specify the items in a display group. [Leaf](pt01ch16pyo04.md) objects are constructed as temporary objects, which are then used as arguments to [DisplayGroup](pt01ch16pyo01.md) commands. 

The LeafFromModelElemLabels object is derived from the [Leaf](pt01ch16pyo04.md) object.

**Access**

```
import displayGroupOdbToolset
```

### 16.17.1 LeafFromModelElemLabels(...)

This method creates a [Leaf](pt01ch16pyo04.md) object from a sequence of element labels spanning several part instances. 

**Path**

```
LeafFromModelElemLabels
```

**Required argument**

*elementLabels*

A sequence of Strings specifying expressions that denote element labels per part instance in the model. Each part instance element expression is a sequence of a String specifying the part instance name and a sequence of element expressions; for example, `(('partInstance1',(1,'7','3:15;3'),), ('partInstance2','8'),))`. The element expressions can be any of the following: 
- An Int specifying a single element label; for example, `1`.
- A String specifying a single element label; for example, `'7'`.
- A String specifying a sequence of element labels; for example, `'3:5'` and `'3:15:3'`.

**Optional arguments**

None.

**Return value**

A LeafFromModelElemLabels object.

**Exceptions**

None.

### 16.17.2 Members

The LeafFromModelElemLabels object has members with the same names and descriptions as the arguments to the [LeafFromModelElemLabels](pt01ch16pyo17.md#ker-leaffrommodelelemlabels-leaffrommodelelemlabels-pyc) method.

In addition, the LeafFromModelElemLabels object has the following member:

*leafType*

A SymbolicConstant specifying the leaf type. Possible values are EMPTY, DEFAULT_MODEL, ALL_ELEMENTS, ALL_NODES, and ALL_SURFACES.




