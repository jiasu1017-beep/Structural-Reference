# 61.25 OdbStep object







An output database contains the same steps of the model database that originated it.

**Access**

```
odb.steps()[*name*]
```

### 61.25.1 Step(...)

This method creates an OdbStep object.

**Path**

```
odb.Step
```

**Prototype**

```
odb_Step&
Step(const odb_String& name,
     const odb_String& description,
     odb_Enum::odb_DomainEnum domain,
     double timePeriod,
     const odb_String& previousStepName,
     const odb_String& procedure,
     double totalTime);
```

**Required arguments**

*name*

An odb_String specifying the repository key.

*description*

An odb_String specifying the step description.

*domain*

An odb_Enum::odb_DomainEnum specifying the domain of the step. Possible values are odb_Enum::TIME, odb_Enum::FREQUENCY, odb_Enum::ARC_LENGTH, and odb_Enum::MODAL.

The type of [OdbFrame](pt02ch61pyo15.md) object that can be created for this step is based on the value of the *domain* argument. 

**Optional arguments**

*timePeriod*

A Double specifying the time period of the step. *timePeriod* is required if *domain*=odb_Enum::TIME; otherwise, this argument is not applicable. The default value is 0.0.

*previousStepName*

An odb_String specifying the preceding step. If *previousStepName* is the empty string, the last step in the repository is used. If *previousStepName* is not the last step, this will result in a change to the *previousStepName* member of the step that was in that position. A special value 'Initial' refers to the internal initial model step and may be used exclusively for inserting a new step at the first position before any other existing steps. The default value is an empty string.

*procedure*

An odb_String specifying the step procedure. The default value is an empty string.

*totalTime*

A Double specifying the analysis time spend in all the steps previous to this step. The default value is 1.0.

**Return value**

An OdbStep object.

**Exceptions**

If *previousStepName* is invalid: 

```
ValueError: previousStepName is invalid
```

### 61.25.2 getFrame(...)

This method retrieves an [OdbFrame](pt02ch61pyo15.md) object associated with a given frame value.

**Prototype**

```
odb_Frame
getFrame(double frameValue,
         odb_Enum::odb_MatchEnum match);
```

**Required argument**

*frameValue*

A Double specifying the value at which the frame is required. *frameValue* can be the step time or frequency.

**Optional argument**

*match*

An odb_Enum::odb_MatchEnum specifying which frame to return if there is no frame at the exact frame value. Possible values are odb_Enum::CLOSEST, odb_Enum::BEFORE, odb_Enum::AFTER, and odb_Enum::EXACT. The default value is odb_Enum::CLOSEST.

When *match*=odb_Enum::CLOSEST, Abaqus returns the closest frame. If the frame value requested is exactly halfway between two frames, Abaqus returns the frame after the value. 

When *match*=odb_Enum::EXACT, Abaqus raises an exception if the exact frame value does not exist.

**Return value**

An [OdbFrame](pt02ch61pyo15.md) object.

**Exceptions**

If the [OdbFrame](pt02ch61pyo15.md) object is not found:

```
OdbError: Frame not found.
```

### 61.25.3 getFrame(...)

This method retrieves an [OdbFrame](pt02ch61pyo15.md) object associated with a given load case.

**Prototype**

```
odb_Frame
getFrame(const odb_LoadCase& loadCase);
```

**Required argument**

*loadCase*

An [OdbLoadCase](pt02ch61pyo17.md) object specifying a load case in the step.

**Optional arguments**

None.

**Return value**

An [OdbFrame](pt02ch61pyo15.md) object.

**Exceptions**

If the [OdbFrame](pt02ch61pyo15.md) object is not found:

```
OdbError: Frame not found.
```

### 61.25.4 getFrame(...)

This method retrieves an [OdbFrame](pt02ch61pyo15.md) object associated with a given load case and frame value.

**Prototype**

```
odb_Frame
getFrame(const odb_LoadCase& loadCase,
         double frameValue,
         odb_Enum::odb_MatchEnum match);
```

**Required arguments**

*loadCase*

An [OdbLoadCase](pt02ch61pyo17.md) object specifying a load case in the step.

*frameValue*

A Double specifying the value at which the frame is required. *frameValue* can be the step time or frequency.

**Optional argument**

*match*

An odb_Enum::odb_MatchEnum specifying which frame to return if there is no frame at the exact frame value. Possible values are odb_Enum::CLOSEST, odb_Enum::BEFORE, odb_Enum::AFTER, and odb_Enum::EXACT. The default value is odb_Enum::CLOSEST.

When *match*=odb_Enum::CLOSEST, Abaqus returns the closest frame. If the frame value requested is exactly halfway between two frames, Abaqus returns the frame after the value. 

When *match*=odb_Enum::EXACT, Abaqus raises an exception if the exact frame value does not exist.

**Return value**

An [OdbFrame](pt02ch61pyo15.md) object.

**Exceptions**

If the [OdbFrame](pt02ch61pyo15.md) object is not found:

```
OdbError: Frame not found.
```

### 61.25.5 getHistoryRegion(...)

This method retrieves a [HistoryRegion](pt02ch61pyo11.md) object associated with a HistoryPoint in the model.

**Prototype**

```
odb_HistoryRegion
getHistoryRegion(const odb_HistoryPoint& point,
                 const odb_LoadCase& loadCase);
```

**Required argument**

*point*

A [HistoryPoint](pt02ch61pyo10.md) object specifying the point in the model.

**Optional argument**

*loadCase*

An [OdbLoadCase](pt02ch61pyo17.md) object specifying a load case in the step.

**Return value**

A [HistoryRegion](pt02ch61pyo11.md) object.

**Exceptions**

If a [HistoryRegion](pt02ch61pyo11.md) object is not found:

```
OdbError: HistoryRegion not found.
```

### 61.25.6 setDefaultDeformedField(...)

This method sets the default deformed field variable in a step.

**Prototype**

```
void
setDefaultDeformedField(const odb_FieldOutput& field);
```

**Required argument**

*field*

A [FieldOutput](pt02ch61pyo07.md) object specifying the default deformed field variable for visualization.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.25.7 setDefaultField(...)

This method sets the default field variable in a step.

**Prototype**

```
void
setDefaultField(const odb_FieldOutput& field);
```

**Required argument**

*field*

A [FieldOutput](pt02ch61pyo07.md) object specifying the default field variable for visualization.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 61.25.8 Members

The OdbStep object has members with the same names and descriptions as the arguments to the [Step](pt02ch61pyo25.md#ker-odbstep-step-cpp) method.

In addition, the OdbStep object can have the following members:

**Prototype**

```
odb_String name() const;
odb_String description() const;
odb_Enum::odb_DomainEnum domain() const;
const odb_LoadCaseRepository& loadCases();
float timePeriod() const;
float totalTime() const;
odb_String previousStepName() const;
odb_String procedure() const;
int number() const;
bool nlgeom() const;
odb_Frame frames(int frameNo);
odb_SequenceFrame& frames();
odb_HistoryRegionRepository& historyRegions();
double mass() const;
odb_SequenceDouble massCenter() const;
odb_SequenceDouble inertiaAboutCenter() const;
odb_SequenceDouble inertiaAboutOrigin() const;
double acousticMass() const;
odb_SequenceDouble acousticMassCenter() const;
odb_SequenceNodalDofs eliminatedNodalDofs() const;

```

*number*

An Int specifying the step number.

*nlgeom*

A Boolean specifying whether geometric nonlinearity can occur in this step.

*mass*

A Double specifying the current value of the mass of the model. This does not include the mass of  the acoustic media if any present.

*acousticMass*

A Double specifying the current value of the mass of the acoustic media of the model.

*frames*

A sequence of [OdbFrame](pt02ch61pyo15.md) objects.

*historyRegions*

A repository of [HistoryRegion](pt02ch61pyo11.md) objects.

*loadCases*

A repository of [OdbLoadCase](pt02ch61pyo17.md) objects.

*massCenter*

An odb_SequenceDouble specifying the coordinates of the center of mass.

*inertiaAboutCenter*

An odb_SequenceDouble specifying the moments and products of inertia about the center of mass. For 3-D models inertia quantities are written in the following order: I(XX), I(YY), I(ZZ), I(XY), I(XZ), and I(YZ). For 2-D models only I(ZZ) and I(XY) are outputted.

*inertiaAboutOrigin*

An odb_SequenceDouble specifying the moments and products of inertia about the origin of the global coordinate system. For 3-D models inertia quantities are written in the following order: I(XX), I(YY), I(ZZ), I(XY), I(XZ), and I(YZ). For 2-D models only I(ZZ) and I(XY) are outputted.

*acousticMassCenter*

An odb_SequenceDouble specifying the coordinates of the center of mass of the acoustic media.




