# 61.15 OdbFrame object







The domain of the OdbFrame object is taken from the parent step.

**Access**

```
odb.steps()[*name*].frames(*i*)
```

### 61.15.1 Frame(...)

This method creates an OdbFrame object and appends it to the frame sequence.

**Path**

```
odb.steps()[*name*].Frame
```

**Prototype**

```
 odb_Frame
                  Frame(int incrementNumber,
                  float frameValue,
                  const odb_String& description);

```

**Required arguments**

*incrementNumber*

An Int specifying the frame increment number within the step. The base frame has normally increment number 0, and the results run from 1. In case of multiple load cases, the same increment number is duplicated for each loadcase.

*frameValue*

A Float specifying the value in units determined by the *domain* member of the [Step](#ker-step-cpp) object. The equivalent in the time domain is *stepTime*; in the frequency domain the equivalent is *frequency*; and in the modal domain the equivalent is *mode*.

**Optional argument**

*description*

An odb_String specifying the contents of the frame. The default value is an empty string.

**Return value**

An OdbFrame object.

**Exceptions**

None.

### 61.15.2 Frame(...)

This constructor creates an OdbFrame object in the frequency domain and appends it to the frame sequence. The arguments to the constructor are valid only when *domain*=FREQUENCY or *domain*=MODAL.

**Path**

```
odb.steps()[*name*].Frame
```

**Prototype**

```
 odb_Frame
                  Frame(int mode,
                  float frequency,
                  const odb_String& description);

```

**Required arguments**

*mode*

An Int specifying the eigenmode. This member is valid only if *domain*=odb_Enum::MODAL.

*frequency*

A Float specifying the frequency. This member is valid only if *domain*=odb_Enum::FREQUENCY or if the *procedureType* member of the [Step](#ker-step-cpp) object=“FREQUENCY”. The default value is 0.0.

**Optional argument**

*description*

An odb_String specifying the contents of the frame. The default value is an empty string.

**Return value**

An OdbFrame object.

**Exceptions**

None.

### 61.15.3 Frame(...)

This constructor creates an OdbFrame object for a specific load case and appends it to the frame sequence. 

**Path**

```
odb.steps()[*name*].Frame
```

**Prototype**

```
 odb_Frame
                  Frame(const odb_LoadCase& loadCase,
                  const odb_String& description,
                  float frequency);

```

**Required argument**

*loadCase*

An [OdbLoadCase](pt02ch61pyo17.md) object specifying the load case for the frame.

**Optional arguments**

*description*

An odb_String specifying the contents of the frame. The default value is an empty string.

*frequency*

A Float specifying the frequency. This member is valid only if *domain*=odb_Enum::FREQUENCY or if the *procedureType* member of the [Step](#ker-step-cpp) object=“FREQUENCY”. The default value is 0.0.

**Return value**

An OdbFrame object.

**Exceptions**

None.

### 61.15.4 Members

The OdbFrame object has members with the same names and descriptions as the arguments to the [Frame](pt02ch61pyo15.md#ker-odbframe-frame-cpp) method.

In addition, the OdbFrame object can have the following members:

**Prototype**

```
odb_Frame associatedFrame();
int cyclicModeNumber();
odb_String description() const;
odb_Enum::odb_DomainEnum domain() const;
odb_FieldOutputRepository& fieldOutputs();
int incrementNumber() const;
float frameValue() const;
float frequency() const;
const odb_LoadCase& loadCase() const;
int mode() const;
```

*cyclicModeNumber*

An Int specifying the cyclic mode number associated with the data stored on this frame. Only frequency analyses of cyclic symmetry models possess cyclic mode numbers.

*domain*

An odb_Enum::odb_DomainEnum specifying the domain of the step of which the frame is a member. Possible values are odb_Enum::TIME, odb_Enum::FREQUENCY, and odb_Enum::MODAL.

*frequency*

A Float specifying the frequency. This member is valid only if *domain*=odb_Enum::FREQUENCY or if the *procedureType* member of the [Step](#ker-step-cpp) object=“FREQUENCY”. The default value is 0.0.

*mode*

An Int specifying the eigenmode. This member is valid only if *domain*=odb_Enum::MODAL.

*associatedFrame*

An OdbFrame object specifying the real or imaginary portion of the data corresponding to this cyclic symmetry mode. 

*fieldOutputs*

A repository of [FieldOutput](pt02ch61pyo07.md) objects specifying the key to the *fieldOutputs*repository is a String representing an output variable.

*loadCase*

An [OdbLoadCase](pt02ch61pyo17.md) object specifying the load case for the frame.




