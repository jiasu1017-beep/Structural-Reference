# 21.5 ExpressionField object







The ExpressionField object defines a spatially varying field whose value is calculated from a user-supplied mathematical expression.

The ExpressionField object is derived from the [AnalyticalField](pt01ch21pyo02.md) object.

**Access**

```
import fields
mdb.models[*name*].analyticalFields[*name*]
```

### 21.5.1 ExpressionField(...)

This method creates an ExpressionField object.

**Path**

```
mdb.models[*name*].ExpressionField
```

**Required arguments**

*name*

A String specifying the repository key.

*expression*

A String specifying the Python expression to evaluate in space. Variables are X, Y, and Z; R, Th, and Z; or R, Th, and P based on the selected coordinate system.

**Optional arguments**

*localCsys*

 `None` or a [DatumCsys](pt01ch15pyo03.md) object specifying the local coordinate system of the field. If *localCsys*=`None`, the field is defined in the global coordinate system. The default value is `None`.

*description*

A String specifying the description of the field. The default value is an empty string.

**Return value**

An ExpressionField object.

**Exceptions**

TextException.

### 21.5.2 setValues(...)

This method modifies the ExpressionField object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ExpressionField](pt01ch21pyo05.md#ker-expressionfield-expressionfield-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

### 21.5.3 Members

The ExpressionField object has members with the same names and descriptions as the arguments to the [ExpressionField](pt01ch21pyo05.md#ker-expressionfield-expressionfield-pyc) method.




