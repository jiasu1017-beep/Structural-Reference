# 60.35 Damping object







The Damping object specifies material damping.

**Access**

```
materialApi.materials()[*name*].damping()
```

### 60.35.1 Damping(...)

This method creates a Damping object.

**Path**

```
materialApi.materials()[*name*].Damping
```

**Prototype**

```
odb_Damping&
Damping(double alpha,
        double beta,
        double composite,
        double structural);
```

**Required arguments**

None.

**Optional arguments**

*alpha*

A Double specifying the ![](../graphics/ker_eqn00161.gif) factor to create mass proportional damping in direct-integration and explicit dynamics. The default value is 0.0.

*beta*

A Double specifying the ![](../graphics/ker_eqn00162.gif) factor to create stiffness proportional damping in direct-integration and explicit dynamics. The default value is 0.0.

*composite*

A Double specifying the fraction of critical damping to be used with this material in calculating composite damping factors for the modes (for use in modal dynamics). The default value is 0.0.

This argument applies only to Abaqus/Standard analyses.

*structural*

A Double specifying the structural factor to create material damping in direct-integration and explicit dynamics. The default value is 0.0.

**Return value**

A Damping object.

**Exceptions**

RangeError.

### 60.35.2 Members

The Damping object has members with the same names and descriptions as the arguments to the [Damping](pt02ch60pyo35.md#ker-damping-damping-cpp) method.

### 60.35.3 Corresponding analysis keywords

| [*DAMPING](../key/key-link.md#usb-kws-mdamping) |
| --- |




