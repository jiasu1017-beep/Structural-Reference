# 63.9 EulerianSection object







The EulerianSection object defines the properties of a Eulerian section.

The EulerianSection object is derived from the [Section](pt02ch63pyo01.md) object.

**Access**

```
sectionApi.sections()[*name*]
```

### 63.9.1 EulerianSection(...)

This method creates a EulerianSection object.

**Path**

```
sectionApi.EulerianSection
```

**Prototype**

```
odb_EulerianSection&
EulerianSection(const odb_String& name,
                const odb_StringRepository& data);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*data*

A repository of String objects specifying a dictionary mapping Material instance names to Material names. Internally the specified mapping gets sorted on Material instance name.

**Optional arguments**

None.

**Return value**

An EulerianSection object.

**Exceptions**

None.

### 63.9.2 Members

The EulerianSection object has members with the same names and descriptions as the arguments to the [EulerianSection](pt02ch63pyo09.md#ker-euleriansection-euleriansection-cpp) method.

### 63.9.3 Corresponding analysis keywords

| [*EULERIAN SECTION](../key/key-link.md#usb-kws-meulsection) |
| --- |




