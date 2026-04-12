# 60.38 Depvar object







The Depvar object specifies solution-dependent state variables.

**Access**

```
materialApi.materials()[*name*].depvar()
```

### 60.38.1 Depvar(...)

This method creates a Depvar object.

**Path**

```
materialApi.materials()[*name*].Depvar
```

**Prototype**

```
odb_Depvar&
Depvar(int deleteVar,
       int n);
```

**Required arguments**

None.

**Optional arguments**

*deleteVar*

An Int specifying the state variable number controlling the element deletion flag. The default value is 0.

This argument applies only to Abaqus/Explicit analyses.

*n*

An Int specifying the number of solution-dependent state variables required at each integration point. The default value is 0.

**Return value**

A Depvar object.

**Exceptions**

RangeError.

### 60.38.2 Members

The Depvar object has members with the same names and descriptions as the arguments to the [Depvar](pt02ch60pyo38.md#ker-depvar-depvar-cpp) method.

### 60.38.3 Corresponding analysis keywords

| [*DEPVAR](../key/key-link.md#usb-kws-mdepvar) |
| --- |




