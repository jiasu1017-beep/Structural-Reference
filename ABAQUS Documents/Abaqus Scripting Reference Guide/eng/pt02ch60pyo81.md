# 60.81 PorousFailureCriteria object







The PorousFailureCriteria object specifies the material failure criteria for a porous metal.

**Access**

```
materialApi.materials()[*name*].porousMetalPlasticity()\
.porousFailureCriteria()
```

### 60.81.1 PorousFailureCriteria(...)

This method creates a PorousFailureCriteria object.

**Path**

```
materialApi.materials()[*name*].porousMetalPlasticity()\
.PorousFailureCriteria
```

**Prototype**

```
odb_PorousFailureCriteria&
PorousFailureCriteria(double fraction,
                      double criticalFraction);
```

**Required arguments**

None.

**Optional arguments**

*fraction*

A Double specifying the void volume fraction at total failure, ![](../graphics/ker_eqn00344.gif). The default value is 1.0.

*criticalFraction*

A Double specifying the critical void volume fraction, ![](../graphics/ker_eqn00345.gif). The default value is 1.0.

**Return value**

A PorousFailureCriteria object.

**Exceptions**

RangeError.

### 60.81.2 Members

The PorousFailureCriteria object has members with the same names and descriptions as the arguments to the [PorousFailureCriteria](pt02ch60pyo81.md#ker-porousfailurecriteria-porousfailurecriteria-cpp) method.

### 60.81.3 Corresponding analysis keywords

| [*POROUS FAILURE CRITERIA](../key/key-link.md#usb-kws-mporfailcriteria) |
| --- |




