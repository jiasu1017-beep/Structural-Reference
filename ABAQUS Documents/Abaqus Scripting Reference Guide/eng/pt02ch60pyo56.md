# 60.56 GasketThicknessBehavior object







The GasketThicknessBehavior object defines the behavior in the thickness direction for a gasket.

**Access**

```
materialApi.materials()[*name*].gasketThicknessBehavior()
```

### 60.56.1 GasketThicknessBehavior(...)

This method creates a GasketThicknessBehavior object.

**Path**

```
materialApi.materials()[*name*].GasketThicknessBehavior
```

**Prototype**

```
odb_GasketThicknessBehavior&
GasketThicknessBehavior(const odb_SequenceSequenceDouble& table,
            bool temperatureDependency,
            int dependencies,
            double tensileStiffnessFactor,
            const odb_String& type,
            int unloadingDependencies,
            bool unloadingTemperatureDependency,
            const odb_String& variableUnits,
            double yieldOnset,
            const odb_String& yieldOnsetMethod,
            const odb_SequenceSequenceDouble& unloadingTable);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying loading data. The first sequence must contain only 0. At least two sequences must be specified if *type*="DAMAGE", and at least 3 sequences must be specified if *type*="ELASTIC_PLASTIC". The items in the table data are described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the loading data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies included in the definition of the loading data, in addition to temperature. The default value is 0.

*tensileStiffnessFactor*

A Double specifying the fraction of the initial compressive stiffness that defines the stiffness in tension. The default value is 10–3.

*type*

An odb_String specifying a damage elasticity model or an elastic-plastic model for gasket thickness-direction behavior. Possible values are "ELASTIC_PLASTIC" and "DAMAGE". The default value is "ELASTIC_PLASTIC".

*unloadingDependencies*

An Int specifying the number of field variable dependencies included in the definition of the unloading data, in addition to temperature. The default value is 0.

*unloadingTemperatureDependency*

A Boolean specifying whether unloading data depends on temperature. The default value is false.

*variableUnits*

An odb_String specifying the behavior in terms of units of force (or force in unit length) versus closure or pressure versus closure. Possible values are "STRESS" and "FORCE". The default value is "STRESS".

*yieldOnset*

A Double specifying the closure value at which the onset of yield occurs or the relative drop in slope on the loading curve that defines the onset of plastic deformation (depending on the value of *yieldOnsetMethod*). The default value is 0.1.

*yieldOnsetMethod*

An odb_String specifying the method used to determine yield onset. Possible values are "RELATIVE_SLOPE_DROP" and "CLOSURE_VALUE". The default value is "RELATIVE_SLOPE_DROP".

*unloadingTable*

An odb_SequenceSequenceDouble specifying unloading data. The items in the table data are described below. The default value is an empty sequence.

**Table data**

If *variableUnits*=STRESS, the loading table data specify the following:
- Pressure; this value must be positive.
- Closure; this value must be positive.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *variableUnits*=FORCE, the loading table data specify the following:- Force or force per unit length; this value must be positive.
- Closure; this value must be positive.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *variableUnits*=STRESS and *type*=ELASTIC_PLASTIC, the *unloadingTable* data specify the following:- Pressure; this value must be positive.
- Closure; this value must be positive.
- Plastic closure; this value must be positive.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *variableUnits*=FORCE and *type*=ELASTIC_PLASTIC, the *unloadingTable* data specify the following:- Pressure; this value must be positive.
- Closure; this value must be positive.
- Plastic closure; this value must be positive.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *variableUnits*=STRESS and *type*=DAMAGE, the *unloadingTable* data specify the following:- Pressure; this value must be positive.
- Closure; this value must be positive.
- Maximum closure reached while loading the gasket; this value must be positive.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *variableUnits*=FORCE and *type*=DAMAGE, the *unloadingTable* data specify the following:- Force or force per unit length; this value must be positive.
- Closure; this value must be positive.
- Maximum closure reached while loading the gasket; this value must be positive.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A GasketThicknessBehavior object.

**Exceptions**

RangeError.

### 60.56.2 Members

The GasketThicknessBehavior object has members with the same names and descriptions as the arguments to the [GasketThicknessBehavior](pt02ch60pyo56.md#ker-gasketthicknessbehavior-gasketthicknessbehavior-cpp) method.

In addition, the GasketThicknessBehavior object can have the following member:

**Prototype**

```
odb_ContactArea contactArea() const;
```

*contactArea*

A [ContactArea](pt02ch60pyo25.md) object.

### 60.56.3 Corresponding analysis keywords

| [*GASKET THICKNESS BEHAVIOR](../key/key-link.md#usb-kws-mgasketnormal) |
| --- |




