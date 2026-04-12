# 60.62 Hypoelastic object







The Hypoelastic object specifies hypoelastic material properties.

**Access**

```
materialApi.materials()[*name*].hypoelastic()
```

### 60.62.1 Hypoelastic(...)

This method creates a Hypoelastic object.

**Path**

```
materialApi.materials()[*name*].Hypoelastic
```

**Prototype**

```
odb_Hypoelastic&
Hypoelastic(const odb_SequenceSequenceDouble& table,
            bool user);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional argument**

*user*

A Boolean specifying that hypoelasticity is defined by user subroutine [`UHYPEL`](../sub/sub-link.md#sub-xsl-uhypel). The default value is false.

**Table data**

- Instantaneous Young's modulus, ![](../graphics/ker_eqn00163.gif).
- Instantaneous Poisson's ratio, ![](../graphics/ker_eqn00164.gif).
- First strain invariant, ![](../graphics/ker_eqn00285.gif).
- Second strain invariant, ![](../graphics/ker_eqn00286.gif).
- Third strain invariant, ![](../graphics/ker_eqn00287.gif).

**Return value**

A Hypoelastic object.

**Exceptions**

None.

### 60.62.2 Members

The Hypoelastic object has members with the same names and descriptions as the arguments to the [Hypoelastic](pt02ch60pyo62.md#ker-hypoelastic-hypoelastic-cpp) method.

### 60.62.3 Corresponding analysis keywords

| [*HYPOELASTIC](../key/key-link.md#usb-kws-mhypoelastic) |
| --- |




