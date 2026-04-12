# 63.24 TransverseShearBeam object







The TransverseShearBeam object defines the transverse shear stiffness properties of a beam section.

**Access**

```
sectionApi.sections()[*name*].beamTransverseShear()
```

### 63.24.1 TransverseShearBeam(...)

This method creates a TransverseShearBeam object.

**Path**

```
sectionApi.sections()[*name*].TransverseShearBeam
```

**Prototype**

```
odb_TransverseShearBeam&
TransverseShearBeam(const odb_String& scfDefinition,
                    odb_Union k23,
                    odb_Union k13,
                    odb_Union slendernessCompensation);
```

**Required argument**

*scfDefinition*

An odb_String specifying how slenderness compensation factor of the section is given. Possible values are "ANALYSIS_DEFAULT", "COMPUTED", and "VALUE".

**Optional arguments**

*k23*

The string "NONE" or a Double specifying the k23 shear stiffness of the section. The default value is "NONE".

*k13*

The string "NONE" or a Double specifying the k13 shear stiffness of the section. The default value is "NONE".

*slendernessCompensation*

The string "COMPUTED" or a Double specifying the slenderness compensation factor of the section. The default value is 0.25.

**Return value**

A TransverseShearBeam object.

**Exceptions**

None.

### 63.24.2 Members

The TransverseShearBeam object has members with the same names and descriptions as the arguments to the [TransverseShearBeam](pt02ch63pyo24.md#ker-transverseshearbeam-transverseshearbeam-cpp) method.

### 63.24.3 Corresponding analysis keywords

| [*TRANSVERSE SHEAR STIFFNESS](../key/key-link.md#usb-kws-mtransshearstiff) |
| --- |




