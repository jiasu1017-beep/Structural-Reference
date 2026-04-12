# 35.1 OdbDisplay object







The OdbDisplay object stores the context of an output database for a viewport. The OdbDisplay object has no constructor. Abaqus creates the *defaultOdbDisplay* member when you import the Visualization module. Abaqus creates the *odbDisplay* member when a viewport is created, using the attributes from the previous active viewport. The previous active viewport contains the attributes from the *defaultOdbDisplay* object for the session. The attributes from the *defaultOdbDisplay* object are copied from the previous active viewport to create the new viewport.

 OdbDisplay objects are accessed in one of two ways: 
- The default output database display options. These settings are used as defaults when other *odbDisplay* members are created and can be set to customize user preferences.
- The output database display options associated with a particular viewport.

**Access**

```
session.viewports[*name*].layers[*name*].odbDisplay
import visualization
session.viewports[*name*].odbDisplay
```

### 35.1.1 moveCameraToCsys()

This method specifies a new position for the camera. It is available only when *movieMode*=ON (in the [View](pt01ch54pyo01.md) object). The new camera position is the origin of the coordinate system specified by the *cameraCsysName* member of the [BasicOptions](pt01ch40pyo01.md) object.

**Arguments**

None.

**Return value**

None

**Exceptions**

None.

### 35.1.2 setDeformedVariable(...)

This method specifies the field output variable or FieldOutput object to be used when displaying the deformed shape of the model.

**Required arguments**

One of the following two mutually exclusive arguments must be provided:

*variableLabel*

A String specifying the field output variable.

*field*

A String specifying the [FieldOutput](pt01ch34pyo06.md) object. 

**Optional arguments**

None.

**Return value**

None

**Exceptions**

If the viewport is not associated with any Odb object:

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.3 setFrame(...)

This method specifies the step and frame for the OdbDisplay object.

**Required arguments**

*step*

An Int specifying the step index. Possible values are 0 ![](../graphics/ker_eqn00013.gif) *step* ![](../graphics/ker_eqn00013.gif) (*numSteps * 1).

*frame*

An Int specifying the frame in the specified step. Valid values are 0 ![](../graphics/ker_eqn00013.gif) *frame* ![](../graphics/ker_eqn00013.gif) (*numFramesInStep * 1). If *frame* ![](../graphics/ker_eqn00407.gif) (*numFramesInStep * 1) the last frame will be displayed.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

If the viewport is not associated with any Odb object:

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

If the Odb object does not contain valid step data:

```
There are no valid step data on the odb. Requested operation cancelled.
```

If an invalid step index is passed in as argument:

```
Invalid step index:step.  Available step indices: 0 - n
```

### 35.1.4 setFrame(...)

This method specifies the frame for the OdbDisplay object.

**Required argument**

*frame*

An OdbFrame object.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 35.1.5 setPrimaryVariable(...)

This method specifies the field output variable for which to obtain results.

**Required arguments**

*variableLabel*

A String specifying the field output variable. The *variableLabel* and *field* arguments are mutually exclusive.

*field*

A String specifying the FieldOutput object. The *variableLabel* and *field* arguments are mutually exclusive.

*outputPosition*

A SymbolicConstant specifying the position from which to obtain data. Possible values are NODAL, INTEGRATION_POINT, ELEMENT_FACE, ELEMENT_NODAL, ELEMENT_CENTROID, WHOLE_ELEMENT, WHOLE_REGION, WHOLE_PART_INSTANCE, WHOLE_MODEL, and GENERAL_PARTICLE. Data can be obtained only from the position at which they were written to the output database during the analysis.

**Optional arguments**

*refinement*

A sequence of a SymbolicConstant and a String. Possible values for the SymbolicConstant are INVARIANT and COMPONENT. The String specifies an available component or invariant for the specified *variableLabel*. This argument is required only if a refinement is available for the specified *variableLabel*.

*sectionPoint*

A Dictionary with String keys and String values. Each key specifies a region in the model; the corresponding value specifies a section point within that region. For example:

```

sectionPoint={'shell < MAT > < 7 section points >':'SPOS,
    (fraction = 1.0)', 'shell < MAT > < 5 section points >':
    'SPOS, (fraction = 1.0)', }
```

**Return value**

None

**Exceptions**

If the viewport is not associated with any Odb object:

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.6 setPrimarySectionPoint(...)

This method specifies the section point for the current primary, symbol and status variables.

**Required arguments**

*sectionPoint*

A Dictionary with String keys and String values. Each key specifies a region in the model; the corresponding value specifies a section point within that region. For example:

```

sectionPoint={'shell < MAT > < 7 section points >':'SPOS,
    (fraction = 1.0)', 'shell < MAT > < 5 section points >':
    'SPOS, (fraction = 1.0)', }
```

*activePly*

A String specifying the active ply name.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

If the viewport is not associated with any Odb object:

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.7 setStatusVariable(...)

This method specifies the field output variable for filtering element display based on a status criteria.

**Required arguments**

*variableLabel*

A String specifying the field output variable. The *variableLabel* and *field* arguments are mutually exclusive.

*field*

A String specifying the FieldOutput object. The *variableLabel* and *field* arguments are mutually exclusive.

*outputPosition*

A SymbolicConstant specifying the position from which to obtain data. Possible values are NODAL, INTEGRATION_POINT, ELEMENT_FACE, ELEMENT_NODAL, ELEMENT_CENTROID, WHOLE_ELEMENT, WHOLE_REGION, WHOLE_PART_INSTANCE, WHOLE_MODEL, and GENERAL_PARTICLE. Data can be obtained only from the position at which they were written to the output database during the analysis.

**Optional arguments**

*refinement*

A sequence of a SymbolicConstant and a String. Possible values for the SymbolicConstant are INVARIANT and COMPONENT. The String specifies an available component or invariant for the specified *variableLabel*. This argument is required only if a refinement is available for the specified *variableLabel*.

*sectionPoint*

A Dictionary with String keys and String values. Each key specifies a region in the model; the corresponding value specifies a section point within that region. For example:

```

sectionPoint={'shell < MAT > < 7 section points >':'SPOS,
    (fraction = 1.0)', 'shell < MAT > < 5 section points >':
    'SPOS, (fraction = 1.0)', }
```

*statusMinimum*

A Float specifying the minimum result value to be considered for element removal.

*statusMaximum*

A Float specifying the maximum result value to be considered for element removal.

*statusInsideRange*

A Boolean utilized when both *statusMinimum* and *statusMaximum* are given.  Elements will be removed when they contain values between the minimum and maximum, inclusive, when true.  Elements will be removed when they contain values outside of the minimum and maximum, exclusive, when false.

*useStatus*

A Boolean to specify if the status variable is to be active.

*applyStatusToUndeformed*

A Boolean to specify if the active status variable is to remove elements from undeformed plots.  The default value is False.

**Return value**

None

**Exceptions**

If the viewport is not associated with any Odb object:

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.8 setSymbolVariable(...)

This method specifies the field output variable for which to obtain results used for symbol plots. This variable must be in the form of vector or tensor data.  The output quantity can also be specified with this command to control the display of resultants, or components.

**Required arguments**

*variableLabel*

A String specifying the field output variable. The *variableLabel* and *field* arguments are mutually exclusive.

*field*

A String specifying the FieldOutput object. The *variableLabel* and *field* arguments are mutually exclusive.

*outputPosition*

A SymbolicConstant specifying the position from which to obtain data. Possible values are NODAL, INTEGRATION_POINT, ELEMENT_FACE, ELEMENT_NODAL, ELEMENT_CENTROID, WHOLE_ELEMENT, WHOLE_REGION, WHOLE_PART_INSTANCE, WHOLE_MODEL, and GENERAL_PARTICLE. Data can be obtained only from the position at which they were written to the output database during the analysis.

**Optional arguments**

*refinement*

A sequence of a SymbolicConstant and a String. Possible values for the SymbolicConstant are INVARIANT and COMPONENT. The String specifies an available component or invariant for the specified *variableLabel*. This argument is required only if a refinement is available for the specified *variableLabel*.

*sectionPoint*

A Dictionary with String keys and String values. Each key specifies a region in the model; the corresponding value specifies a section point within that region. For example:

```

sectionPoint={'shell < MAT > < 7 section points >':'SPOS,
    (fraction = 1.0)', 'shell < MAT > < 5 section points >':
    'SPOS, (fraction = 1.0)', }
```

*tensorQuantity*

A SymbolicConstant specifying the tensor quantity to be displayed with the symbol.  This value is set in the [SymbolOptions](pt01ch35pyo08.md) object.

*vectorQuantity*

A SymbolicConstant specifying the vector quantity to be displayed with the symbol.  This value is set in the [SymbolOptions](pt01ch35pyo08.md) object.

**Return value**

None

**Exceptions**

If the viewport is not associated with any Odb object:

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.9 setStreamVariable(...)

This method specifies the field output variable for which to obtain results used for stream plots. This variable must be in the form of nodal vector data.

**Required argument**

*variableLabel*

A String specifying the field output variable.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

If the viewport is not associated with any Odb object:

```
The current viewport is not associated with an ODB file. Requested operation cancelled.
```

### 35.1.10 setValues(...)

This method specifies member values for the OdbDisplay object.

**Required arguments**

None.

**Optional arguments**

*visibleDisplayGroups*

A List of [DisplayGroup](pt01ch16pyo01.md) objects.

*viewCut*

A Boolean specifying whether to display the cut. The default value is OFF.

*viewCutNames*

A List of [ViewCut](pt01ch35pyo09.md) objects.

**Return value**

None

**Exceptions**

None.

### 35.1.11 Members

The OdbDisplay object can have the following members:

*name*

A String specifying the name of the output database associated with the OdbDisplay object.

*fieldSteps*

A tuple of Strings specifying field steps.

Each item in the sequence consists of a tuple that contains the following step information:
- *element0*: A String specifying the step name.
- *element1*: A String specifying the step description.
- *element2*: A Float specifying the time value at the start of the step.
- *element3*: A Float specifying the time period of the step.
- *element4*: A Float specifying the user modified time period of the step.
- *element5*: An Int specifying the domain type of the step. Possible values are: - 0: Time domain - 1: Frequency domain - 2: Modal domain - 3: Arc Length (Riks) domain
- *element6*: A String specifying the default frame label.
- *element7*: A sequence of strings specifying the frame labels for all available frames in the step.
- *element8*: A sequence of floats specifying the frame values for all available frames in the step.
- *element9*: A Int specifying whether the step is user defined. Possible values are 0 indicating the step is defined in the analysis and 1 indicating the step is user defined.
- *element10*: A sequence of machine readable strings encoding the currently active frame numbers.

*fieldVariables*

An [OdbFieldVarList](pt01ch23pyo03.md) object.

*modelVariableList*

An [OdbModelFieldVarList](pt01ch23pyo04.md) object.

*nodeSet*

A repository of [OdbSet](pt01ch34pyo23.md) objects specifying the set label. The repository is read-only.

*elementSet*

A repository of [OdbSet](pt01ch34pyo23.md) objects specifying the set label. The repository is read-only.

*surfaceSet*

A repository of [OdbSet](pt01ch34pyo23.md) objects specifying the set label. The repository is read-only.

*display*

A [DisplayOptions](pt01ch40pyo04.md) object.

*contourOptions*

A [ContourOptions](pt01ch35pyo03.md) object.

*commonOptions*

A [CommonOptions](pt01ch35pyo02.md) object.

*symbolOptions*

A [SymbolOptions](pt01ch35pyo08.md) object.

*superimposeOptions*

A [SuperimposeOptions](pt01ch35pyo07.md) object.

*displayBodyOptions*

A [DisplayBodyOptions](pt01ch35pyo05.md) object.

*freeBodyOptions*

A [FreeBodyOptions](pt01ch40pyo06.md) object.

*streamOptions*

A [StreamOptions](pt01ch40pyo21.md) object.

*viewCutOptions*

A [ViewCutOptions](pt01ch40pyo24.md) object.

*viewCuts*

A repository of [ViewCut](pt01ch35pyo09.md) objects.

*displayGroup*

A [DisplayGroup](pt01ch16pyo01.md) object specifying the current display group and referring to an object in the *displayGroups* member of [Session](pt01ch47pyo01.md).

*displayGroupInstances*

A [DisplayGroupInstanceRepository](pt01ch16pyo03.md) object.

*basicOptions*

A [BasicOptions](pt01ch40pyo01.md) object.

*materialOrientationOptions*

An [OrientationOptions](pt01ch35pyo06.md) object.

*fieldFrame*

A tuple of Strings specifying the step label and the frame label when the current step is user defined. Alternatively, *fieldFrame* maybe specified as a pair of Ints with the step index and the frame index, when the current step is defined in the analysis.

*primaryVariable*

A tuple specifying variables.

Each item in the sequence consists of a tuple containing the following elements:
- Element 0: A String specifying the variable label.
- Element 1: An Int specifying the output position. Possible integer values are: - 0: UNDEFINED_POSITION - 1: NODAL - 2: INTEGRATION_POINT - 3: ELEMENT_FACE - 4: ELEMENT_NODAL - 5: WHOLE_ELEMENT - 6: ELEMENT_CENTROID - 7: WHOLE_REGION - 8: WHOLE_PART_INSTANCE - 9: WHOLE_MODEL - 10: GENERAL_PARTICLE
- Element 2: An Int specifying the data type. Possible values are: - 0: ENUMERATION - 1: BOOLEAN - 2: INTEGER - 3: SCALAR - 4: VECTOR - 5: QUATERNION_2D - 6: QUATERNION_3D - 7: TENSOR - 8: TENSOR_3D_FULL - 9: TENSOR_3D_PLANAR - 10: TENSOR_3D_SURFACE - 11: TENSOR_2D_PLANAR - 12: TENSOR_2D_SURFACE
- Element 3: An Int specifying the storage type. Possible values are: - 0: FLOAT - 1: DOUBLE - 2: INTEGER - 3: BOOLEAN
- Element 4: An Int specifying the refinement type. Possible values are: - 0: NO_REFINEMENT - 1: INVARIANT - 2: COMPONENT
- Element 5: A String specifying the refinement label.
- Element 6: An Int specifying the refinement index.
- Element 7: An Int specifying whether section point information is available. Possible values are 1 when section point information is available; 0, when this information is unavailable.
- Element 8: A sequence of a String specifying the name of the ply and category selection tuples (see below) specifying the section point information. A category selection tuple consists of the following elements: - Element 0: A String specifying the category label. - Element 1: An Int specifying whether to use both top and bottom section points to obtain results. Possible values are 1 to use both section points and 0 to use only the top section point. - Element 2: An Int specifying the top section point index. - Element 3: A String specifying the top section label. - Element 4: An Int specifying the bottom section point index. - Element 5: A String specifying the bottom section label. - Element 6: An Int specifying the category id.
- Element 9: An Int specifying whether the data are complex. Possible values are 1 when the data are complex; 0, when the data is not complex.
- Element 10: A Float specifying the minimum possible value for the data.
- Element 11: A Float specifying the maximum possible value for the data.
- Element 12: An Int specifying whether the data is derived. Possible values are 1 when the data is derived; 0, when the data is not derived.

*deformedVariable*

A tuple specifying variables.

For information on the sequence, see the member *primaryVariable*.

*statusVariable*

A tuple of SymbolicConstants specifying variables.

For information on the sequence, see the member *primaryVariable*.

*symbolVariable*

A tuple of SymbolicConstants specifying variables.

For information on the sequence, see the member *primaryVariable*.

*applyStatusToUndeformed*

A tuple of SymbolicConstants specifying a Boolean to specify if elements are to be removed in undeformed states based on an active status variable

*statusInsideRange*

A tuple of SymbolicConstants specifying a Boolean to specify if the status range should be inside a specified minimum and maximum.  The range will be outside when false.

*statusMinimum*

A tuple of Floats specifying a Float value for the minimum status range value.

*statusMaximum*

A tuple of Floats specifying a Float value for the maximum status range value.

*useStatus*

A tuple of SymbolicConstants specifying a Boolean to specify if elements are to be removed based on the status variable

*firstFrame*

A pair of Ints specifying the step index and the frame index of the first available frame. This sequence is read-only.

*prevFrame*

A pair of Ints specifying the step index and the frame index of the frame previous to the current frame. This sequence is read-only.

*nextFrame*

A pair of Ints specifying the step index and the frame index of the frame following the current frame. This sequence is read-only.

*lastFrame*

A pair of Ints specifying the step index and the frame index of the last available frame. This sequence is read-only.




