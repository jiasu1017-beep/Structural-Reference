# 63.21 ShellSection object







The ShellSection object defines the properties of a shell section. The ShellSection object is derived from the [Section](pt02ch63pyo01.md) object. The ShellSection object has no explicit constructor and no methods or members.

The ShellSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.21.1 Members

The ShellSection object can have the following members:

**Prototype**

```
odb_String name() const;
odb_TransverseShearShell transverseShear() const;
```

*name*

An odb_String specifying the repository key.

*transverseShear*

A [TransverseShearShell](pt02ch63pyo25.md) object specifying the transverse shear stiffness properties.




