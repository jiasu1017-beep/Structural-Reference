# 60.23 ConcreteTensionStiffening object







The ConcreteTensionStiffening object specifies hardening for the concrete damaged plasticity model.

**Access**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.concreteTensionStiffening()
```

### 60.23.1 ConcreteTensionStiffening(...)

This method creates a ConcreteTensionStiffening object.

**Path**

```
materialApi.materials()[*name*].concreteDamagedPlasticity()\
.ConcreteTensionStiffening
```

**Prototype**

```
odb_ConcreteTensionStiffening&
ConcreteTensionStiffening(const odb_SequenceSequenceDouble& table,
                          bool rate,
                          const odb_String& type,
                          bool temperatureDependency,
                          int dependencies);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*rate*

A Boolean specifying whether the data depend on rate. The default value is false.

*type*

An odb_String specifying the type of postcracking behavior data. Possible values are:
- "STRAIN", specifying postfailure stress as a function of cracking strain.
- "DISPLACEMENT", specifying postfailure stress as a function of cracking displacement.
- "GFI", specifying failure stress as a function of the fracture energy.

The default value is "STRAIN".

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

**Table data**

If *type*=STRAIN, the table data specify the following:
- Remaining direct stress after cracking, ![](../graphics/ker_eqn00104.gif).
- Direct cracking strain, ![](../graphics/ker_eqn00137.gif).
- Direct cracking strain rate, ![](../graphics/ker_eqn00139.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=DISPLACEMENT, the table data specify the following:- Remaining direct stress after cracking, ![](../graphics/ker_eqn00104.gif).
- Direct cracking displacement, ![](../graphics/ker_eqn00138.gif).
- Direct cracking displacement rate, ![](../graphics/ker_eqn00140.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=GFI, the table data specify the following:

- Failure stress, ![](../graphics/ker_eqn00141.gif).
- Fracture energy, ![](../graphics/ker_eqn00142.gif).
- Direct cracking displacement rate, ![](../graphics/ker_eqn00140.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A ConcreteTensionStiffening object.

**Exceptions**

RangeError.

### 60.23.2 Members

The ConcreteTensionStiffening object has members with the same names and descriptions as the arguments to the [ConcreteTensionStiffening](pt02ch60pyo23.md#ker-concretetensionstiffening-concretetensionstiffening-cpp) method.

### 60.23.3 Corresponding analysis keywords

| [*CONCRETE TENSION STIFFENING](../key/key-link.md#usb-kws-mconcretetensstiff) |
| --- |




