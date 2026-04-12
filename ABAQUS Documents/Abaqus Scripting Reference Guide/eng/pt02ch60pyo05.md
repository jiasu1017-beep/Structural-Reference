# 60.5 BrittleCracking object







The BrittleCracking object specifies cracking and postcracking properties for the brittle cracking material model.

**Access**

```
materialApi.materials()[*name*].brittleCracking()
```

### 60.5.1 BrittleCracking(...)

This method creates an BrittleCracking object.

**Path**

```
materialApi.materials()[*name*].BrittleCracking
```

**Prototype**

```
odb_BrittleCracking&
BrittleCracking(const odb_SequenceSequenceDouble& table,
                bool temperatureDependency,
                int dependencies,
                const odb_String& type);
```

**Required argument**

*table*

An odb_SequenceSequenceDouble specifying the items described below.

**Optional arguments**

*temperatureDependency*

A Boolean specifying whether the data depend on temperature. The default value is false.

*dependencies*

An Int specifying the number of field variable dependencies. The default value is 0.

*type*

An odb_String specifying the type of postcracking behavior. Possible values are "STRAIN", "DISPLACEMENT", and "GFI". The default value is "STRAIN".

**Table data**

If *type*=STRAIN the table data specify the following:
- Remaining direct stress after cracking.
- Direct cracking strain.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=DISPLACEMENT the table data specify the following:- Remaining direct stress after cracking.
- Direct cracking displacement.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=GFI the table data specify the following:- Failure stress.
- Mode I fracture energy.
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A BrittleCracking object.

**Exceptions**

None.

### 60.5.2 Members

The BrittleCracking object has members with the same names and descriptions as the arguments to the [BrittleCracking](pt02ch60pyo05.md#ker-brittlecracking-brittlecracking-cpp) method.

In addition, the BrittleCracking object can have the following members:

**Prototype**

```
odb_BrittleShear brittleShear() const;
odb_BrittleFailure brittleFailure() const;
```

*brittleShear*

A [BrittleShear](pt02ch60pyo07.md) object.

*brittleFailure*

A [BrittleFailure](pt02ch60pyo06.md) object.

### 60.5.3 Corresponding analysis keywords

| [*BRITTLE CRACKING](../key/key-link.md#usb-kws-mcracking) |
| --- |




