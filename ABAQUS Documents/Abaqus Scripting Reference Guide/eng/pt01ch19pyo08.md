# 19.8 HeatCapacitance object







The HeatCapacitance object defines point heat capacitance on a part or an assembly region.

The HeatCapacitance object is derived from the [Inertia](pt01ch19pyo09.md) object.

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.inertias[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.inertias[*name*]
```

### 19.8.1 HeatCapacitance(...)

This method creates a HeatCapacitance object.

**Path**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.HeatCapacitance
mdb.models[*name*].rootAssembly.engineeringFeatures.HeatCapacitance
```

**Required arguments**

*name*

A String specifying the repository key.

*region*

A [Region](pt01ch45pyo03.md) object specifying the region to which the heat capacitance is applied.

*table*

A sequence of sequences of Floats specifying heat capacitance properties. The items in the table data are described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

The table data specify the following:
- Heat capacitance magnitude, ![](../graphics/ker_eqn00056.gif) (density specific heat volume).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A HeatCapacitance object.

**Exceptions**

None.

### 19.8.2 setValues(...)

This method modifies the HeatCapacitance object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [HeatCapacitance](pt01ch19pyo08.md#ker-heatcapacitance-heatcapacitance-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 19.8.3 Members

The HeatCapacitance object has members with the same names and descriptions as the arguments to the [HeatCapacitance](pt01ch19pyo08.md#ker-heatcapacitance-heatcapacitance-pyc) method.

In addition, the HeatCapacitance object has the following member:

*suppressed*

A Boolean specifying whether the inertia is suppressed or not. The default value is OFF.

### 19.8.4 Corresponding analysis keywords

| [*HEATCAP](../key/key-link.md#usb-kws-mheatcap) |
| --- |




