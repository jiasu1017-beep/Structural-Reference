# 61.9 HistoryOutput object







The HistoryOutput object contains the history output at a point for the specified variable.

**Access**

```
odb.steps()[*name*].historyRegions()[*name*].historyOutputs()[*name*]
```

### 61.9.1 HistoryOutput(...)

This method creates a HistoryOutput object.

**Path**

```
odb.steps()[*name*].historyRegions()[*name*].HistoryOutput
```

**Prototype**

```
odb_HistoryOutput&
HistoryOutput(const odb_String& name,
              const odb_String& description,
              odb_Enum::odb_DataTypeEnum type,
              const odb_SequenceInvariant& validInvariants);
```

**Required arguments**

*name*

An odb_String specifying the output variable name.

*description*

An odb_String specifying the output variable.

*type*

An odb_Enum::odb_DataTypeEnum specifying the output type. Only odb_Enum::SCALAR is currently supported. 

**Optional argument**

*validInvariants*

An odb_SequenceInvariant specifying which invariants should be calculated for this field. Possible values are odb_Enum::MAGNITUDE, odb_Enum::MISES, odb_Enum::TRESCA, odb_Enum::PRESS, odb_Enum::INV3, odb_Enum::MAX_PRINCIPAL, odb_Enum::MID_PRINCIPAL, and odb_Enum::MIN_PRINCIPAL. The default value is an empty sequence.

**Return value**

A HistoryOutput object.

**Exceptions**

None.

### 61.9.2 addData(...)

This method adds data to the *data* member of the HistoryOutput object.

**Prototype**

```
void
addData(double frame,
        double value);
```

**Required arguments**

*frame*

A Double specifying the frame value. *frame* can be specified in step time, frequency, or mode number.

*value*

A Double specifying the value of the variable at the frame value specified in *frame*.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.9.3 addData(...)

This method adds data to the *data* member of the HistoryOutput object.

**Prototype**

```
void
addData(const odb_SequenceFloat& frame,
        const odb_SequenceFloat& value);
```

**Required arguments**

*frame*

An odb_SequenceFloat specifying the frame values. *frame* can be specified in step time, frequency, or mode number.

*value*

An odb_SequenceFloat specifying the value of the variable at the frame values specified in *frame*.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

If the length of *frame* is not the same as the length of *value* a ValueError is raised.

### 61.9.4 addData(...)

This method adds data to the *data* member of the HistoryOutput object.

**Prototype**

```
void
addData(const odb_SequenceSequenceFloat& data);
```

**Required argument**

*data*

An odb_SequenceSequenceFloat specifying the pairs (*frameValue*, *value*) where *frameValue* is either time, frequency, or mode and *value* is the value of the specified variable at *frameValue*. (This value depends on the type of the variable.)

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.9.5 Members

The HistoryOutput object has members with the same names and descriptions as the arguments to the [HistoryOutput](pt02ch61pyo09.md#ker-historyoutput-historyoutput-cpp) method.

In addition, the HistoryOutput object has the following members:

**Prototype**

```
odb_String name() const;
odb_String description() const;
odb_SequenceSequenceFloat data() const;
odb_SequenceSequenceFloat conjugateData() const;
```

*data*

An odb_SequenceSequenceFloat specifying the pairs (*frameValue*, *value*) where *frameValue* is either time, frequency, or mode and *value* is the value of the specified variable at *frameValue*. (This value depends on the type of the variable.)

*conjugateData*

An odb_SequenceSequenceFloat specifying the imaginary portion of a specified complex variable at each frame value (time, frequency, or mode). The pairs have the form (*frameValue*, *value*).




