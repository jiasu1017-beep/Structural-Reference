# 63.25 TransverseShearShell object







The TransverseShearShell object defines the transverse shear stiffness properties of a shell section.

**Access**

```
sectionApi.sections()[*name*].transverseShear()
```

### 63.25.1 TransverseShearShell(...)

This method creates a TransverseShearShell object.

**Path**

```
sectionApi.sections()[*name*].TransverseShearShell
```

**Prototype**

```
odb_TransverseShearShell&
TransverseShearShell(double k11,
                     double k22,
                     double k12);
```

**Required arguments**

*k11*

A Double specifying the shear stiffness of the section in the first direction.

*k22*

A Double specifying the shear stiffness of the section in the second direction.

*k12*

A Double specifying the coupling term in the shear stiffness of the section.

**Optional arguments**

None.

**Return value**

A TransverseShearShell object.

**Exceptions**

None.

### 63.25.2 Members

The TransverseShearShell object has members with the same names and descriptions as the arguments to the [TransverseShearShell](pt02ch63pyo25.md#ker-transverseshearshell-transverseshearshell-cpp) method.

### 63.25.3 Corresponding analysis keywords

| [*TRANSVERSE SHEAR STIFFNESS](../key/key-link.md#usb-kws-mtransshearstiff) |
| --- |




