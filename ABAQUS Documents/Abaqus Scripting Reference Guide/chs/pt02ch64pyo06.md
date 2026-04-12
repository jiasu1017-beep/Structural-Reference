# 64.6 Union object







An odb_Union object is used to determine the type of variable used when an object allows multiple variable types. The odb_Union object can have a value that is either a SymbolicConstant, Int, Float, Double, Boolean, or String.

### 64.6.1 type(...)

This method returns the current type of the odb_Union object.

**Prototype**

```
odb_UnionType type();
```

**Return value**

The type of the odb_Union object. Possible values are odb_UNION_INT, odb_UNION_FLOAT, odb_UNION_DOUBLE, odb_UNION_BOOL, and odb_UNION_STRING.

**Exceptions**

odbException

None.



