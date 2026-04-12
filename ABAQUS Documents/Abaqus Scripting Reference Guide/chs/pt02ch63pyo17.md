# 63.17 MPCSection object







The MPCSection object defines the properties of a multi-point constraint section.

The MPCSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.17.1 MPCSection(...)

This method creates a MPCSection object.

**Path**

```
sectionApi.MPCSection
```

**Prototype**

```
odb_MPCSection&
MPCSection(const odb_String& name,
           const odb_String& mpcType,
           const odb_String& userMode,
           int userType);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*mpcType*

An odb_String specifying the MPC type of the section. Possible values are "BEAM_MPC", "ELBOW_MPC", "PIN_MPC", "LINK_MPC", "TIE_MPC", and "USER_DEFINED".

**Optional arguments**

*userMode*

An odb_String specifying the mode of the MPC when it is user-defined. Possible values are "DOF_MODE" and "NODE_MODE". The default value is "DOF_MODE".

The *userMode* argument applies only when *mpcType*="USER_DEFINED".

*userType*

An Int specifying to differentiate between different constraint types in a user-defined MPCSection. The default value is 0.

The *userType* argument applies only when *mpcType*="USER_DEFINED".

**Return value**

A MPCSection object.

**Exceptions**

RangeError and InvalidNameError.

### 63.17.2 Members

The MPCSection object has members with the same names and descriptions as the arguments to the [MPCSection](pt02ch63pyo17.md#ker-mpcsection-mpcsection-cpp) method.

### 63.17.3 Corresponding analysis keywords

| [*MPC](../key/key-link.md#usb-kws-mmpc) |
| --- |




