# 44.2 CompositeLayup object







The CompositeLayup object is used to specify a composite layup on a part.

**Access**

```
import part
mdb.models[*name*].parts[*name*].compositeLayups[*i*]
```

### 44.2.1 CompositeLayup(...)

This method creates a CompositeLayup object.

**Path**

```
mdb.models[*name*].parts[*name*].CompositeLayups
```

**Required argument**

*name*

A String specifying the repository key.

**Optional arguments**

*description*

A String specifying a description of the composite layup.

*offsetType*

A SymbolicConstant specifying the method used to define the shell offset. If *offsetType*=OFFSET_FIELD the *offsetField* argument is required.                      This member is valid only if *elementType*=SHELL. Possible values are SINGLE_VALUE, MIDDLE_SURFACE, TOP_SURFACE, BOTTOM_SURFACE, OFFSET_FIELD, and GLOBAL. The default value is GLOBAL.

*offsetField*

A String specifying                      The name of the field specifying the offset.                     This member is valid only if *elementType*=SHELL.                    The default value is an empty string.

*offsetValues*

A Float specifying                   The offset of the shell section.                  This member is valid only if *elementType*=SHELL.                 The default value is 0.0.

*elementType*

A SymbolicConstant specifying the type of element in the composite layup. Possible values are SHELL, CONTINUUM_SHELL, and SOLID. The default value is SHELL.

*symmetric*

A Boolean specifying whether or not the layup should be made symmetric by the analysis. The default value is OFF.

**Return value**

A CompositeLayup object.

**Exceptions**

AbaqusException.

### 44.2.2 suppress()

This method suppresses a composite layup.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 44.2.3 resume()

This method resumes a composite layup that was previously suppressed.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 44.2.4 deletePlies()

This method deletes all of the plies from a composite layup.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 44.2.5 setValues(...)

This method modifies the CompositeLayup object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CompositeLayup](pt01ch44pyo02.md#ker-compositelayup-compositelayup-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 44.2.6 Members

The CompositeLayup object has members with the same names and descriptions as the arguments to the [CompositeLayup](pt01ch44pyo02.md#ker-compositelayup-compositelayup-pyc) method.

In addition, the CompositeLayup object has the following members:

*section*

A [GeometryShellSection](pt01ch46pyo12.md) object.

*orientation*

A [MaterialOrientation](pt01ch44pyo04.md) object.

*plies*

A [CompositePlyArray](pt01ch44pyo03.md) object specifying the plies that make up this composite layup.

### 44.2.7 Corresponding analysis keywords

| [*SHELL SECTION](../key/key-link.md#usb-kws-mshellsection) |
| --- |
| [*SHELL GENERAL SECTION](../key/key-link.md#usb-kws-mshellgensect) |
| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |




