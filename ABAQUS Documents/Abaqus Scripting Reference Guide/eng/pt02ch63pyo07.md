# 63.7 CompositeSolidSection object







The CompositeSolidSection object defines the properties of a composite solid section.

The CompositeSolidSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.7.1 CompositeSolidSection(...)

This method creates a CompositeSolidSection object.

**Path**

```
sectionApi.CompositeSolidSection
```

**Prototype**

```
odb_CompositeSolidSection&
CompositeSolidSection(const odb_String& name,
                      const odb_SequenceSectionLayer& layup,
                      bool symmetric,
                      const odb_String& layupName);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*layup*

A sequence of [SectionLayer](pt02ch63pyo20.md) objects specifying the solid cross-section.

**Optional arguments**

*symmetric*

A Boolean specifying whether or not the layup should be made symmetric by the analysis. The default value is false.

*layupName*

An odb_String specifying the layup name for this section. The default value is an empty string.

**Return value**

A CompositeSolidSection object.

**Exceptions**

None.

### 63.7.2 Members

The CompositeSolidSection object has members with the same names and descriptions as the arguments to the [CompositeSolidSection](pt02ch63pyo07.md#ker-compositesolidsection-compositesolidsection-cpp) method.

### 63.7.3 Corresponding analysis keywords

| [*SOLID SECTION](../key/key-link.md#usb-kws-msolidsection) |
| --- |




