# 29.25 ContactArea object







A ContactArea object specifies a suboption of gasket thickness behavior when *variableUnits*=FORCE on the GasketThicknessBehavior object. The ContactArea object defines the contact area or contact width versus closure curves to output an average pressure through variable CS11.

**Access**

```
import material
mdb.models[*name*].materials[*name*].gasketThicknessBehavior.contactArea
import odbMaterial
session.odbs[*name*].materials[*name*].gasketThicknessBehavior.contactArea
```

### 29.25.1 ContactArea(...)

This method creates a ContactArea object.

**Path**

```
mdb.models[*name*].materials[*name*].gasketThicknessBehavior.ContactArea
session.odbs[*name*].materials[*name*].gasketThicknessBehavior.ContactArea
```

**Required argument**

*table*

A sequence of sequences of Floats specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether contact area data depend on temperature. The default value is OFF.

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

### 29.25.2 setValues(...)

This method modifies the ContactArea object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [ContactArea](pt01ch29pyo25.md#ker-contactarea-contactarea-pyc) method.

**Return value**

None

**Exceptions**

None.

### 29.25.3 Members

The ContactArea object has members with the same names and descriptions as the arguments to the [ContactArea](pt01ch29pyo25.md#ker-contactarea-contactarea-pyc) method.

### 29.25.4 Corresponding analysis keywords

| [*GASKET CONTACT AREA](../key/key-link.md#usb-kws-mgasketcontactarea) |
| --- |




