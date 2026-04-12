# 60.25 ContactArea object







A ContactArea object specifies a suboption of gasket thickness behavior when *variableUnits*=FORCE on the GasketThicknessBehavior object. The ContactArea object defines the contact area or contact width versus closure curves to output an average pressure through variable CS11.

**Access**

```
materialApi.materials()[*name*].gasketThicknessBehavior().contactArea()
```

### 60.25.1 ContactArea(...)

This method creates a ContactArea object.

**Path**

```
materialApi.materials()[*name*].gasketThicknessBehavior().ContactArea
```

**Prototype**

```
odb_ContactArea&
ContactArea(const odb_SequenceSequenceDouble& table,
            bool temperatureDependency,
            int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether contact area data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies included in the definition of the contact area data, in addition to temperature. The default value is 0.

**Table data**

- Contact area or width; this value must be positive.
- Closure; this value must be positive.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ContactArea object.

**Exceptions**

None.

### 60.25.2 Members

The ContactArea object has members with the same names and descriptions as the arguments to the [ContactArea](pt02ch60pyo25.md#ker-contactarea-contactarea-cpp) method.

### 60.25.3 Corresponding analysis keywords

| [*GASKET CONTACT AREA](../key/key-link.md#usb-kws-mgasketcontactarea) |
| --- |




