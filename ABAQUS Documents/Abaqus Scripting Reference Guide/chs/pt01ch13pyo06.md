# 13.6 Equation object







The Equation object defines a linear multi-point constraint between a set of degrees of freedom.

The Equation object is derived from the [Constraint](pt01ch13pyo01.md) object.

**Access**

```
import interaction
mdb.models[*name*].constraints[*name*]
```

### 13.6.1 Equation(...)

This method creates an Equation object.

**Path**

```
mdb.models[*name*].Equation
```

**Required arguments**

*name*

A String specifying the constraint repository key.

*terms*

A sequence of (Float, String, Int, Int) sequences specifying a coefficient, Set name, degree of freedom, and coordinate system ID. The coordinate system ID is optional.

**Optional arguments**

None.

**Return value**

An Equation object.

**Exceptions**

If *terms* does not contain more than one entry:

```
Equation must have two or more terms.
```

### 13.6.2 setValues(...)

This method modifies the Equation object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [Equation](pt01ch13pyo06.md#ker-equation-equation-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

If *terms* does not contain more than one entry:

```
Equation must have two or more terms.
```

### 13.6.3 Members

The Equation object has members with the same names and descriptions as the arguments to the [Equation](pt01ch13pyo06.md#ker-equation-equation-pyc) method.

In addition, the Equation object has the following member:

*suppressed*

A Boolean specifying whether the constraint is suppressed or not. The default value is OFF.

### 13.6.4 Corresponding analysis keywords

| [*EQUATION](../key/key-link.md#usb-kws-mequation) |
| --- |




