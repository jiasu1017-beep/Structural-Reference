# 17.1 AssemblyDisplayOptions object







The AssemblyDisplayOptions object stores settings that specify how assemblies are to be displayed in a particular viewport. The AssemblyDisplayOptions object has no constructor. When you create a new viewport, the settings are copied from the current viewport.

**Access**

```
import assembly
session.viewports[*name*].assemblyDisplay
session.viewports[*name*].layers[*name*].assemblyDisplay
```

### 17.1.1 setValues(...)

This method modifies the AssemblyDisplayOptions object.

**Required arguments**

None.

**Optional arguments**

*visibleInstances*

A sequence of Strings specifying the names of the part instances that are visible in the viewport. The default value is an empty sequence.

*step*

A String specifying the step for which objects are to be displayed. Possible values are any valid step name. The default value is "Initial".

*renderStyle*

A SymbolicConstant specifying how the image in the viewport is rendered. Possible values are WIREFRAME, HIDDEN, SHADED, and FILLED. The default value is WIREFRAME.

*mesh*

A Boolean specifying whether the mesh is shown. The default value is OFF.

*loads*

A Boolean specifying whether loads are shown. The default value is OFF.

*bcs*

A Boolean specifying whether boundary conditions are shown. The default value is OFF.

*interactions*

A Boolean specifying whether interactions are shown. The default value is OFF.

*constraints*

A Boolean specifying whether constraints are shown. The default value is OFF.

*connectors*

A Boolean specifying whether connectors are shown. The default value is OFF.

*cnxEndPoints*

A Boolean specifying whether the connector end points are shown. This member is applicable only if *connectors*=ON. The default value is ON.

*cnxLocalAxes*

A Boolean specifying whether the connector local coordinate system axes are shown. This member is applicable only if *connectors*=ON. The default value is ON.

*cnxTypeLabels*

A Boolean specifying whether the connector section type labels are shown. This member is applicable only if *connectors*=ON. The default value is ON.

*cnxTagDisplay*

A Boolean specifying whether the tag information is displayed along with the connector section type labels. This member is applicable only if *connectors*=ON and if *cnxTypeLabels*=ON. The default value is OFF.

*predefinedFields*

A Boolean specifying whether fields and initial conditions are shown. The default value is OFF.

*visibleDisplayGroups*

A sequence of [DisplayGroup](pt01ch16pyo01.md) objects specifying the DisplayGroups visible in the viewport. Currently the sequence can contain a maximum of one [DisplayGroup](pt01ch16pyo01.md) object. The default value is an empty sequence.

*engineeringFeatures*

A Boolean specifying whether to display engineering features. The default value is OFF.

*renderBeamProfiles*

A Boolean specifying whether to render the beam profiles. The default value is OFF.

*beamScaleFactor*

A Float specifying the beam profile scale factor. The beamScaleFactor must be greater than zero. The default value is 1.0.

*optimizationTasks*

A Boolean specifying whether optimization tasks are shown. The default value is OFF.

*geometricRestrictions*

A Boolean specifying whether geometric restrictions are shown. The default value is OFF.

*stopConditions*

A Boolean specifying whether stop conditions are shown. The default value is OFF.

**Return value**

None

**Exceptions**

RangeError.

### 17.1.2 Members

The AssemblyDisplayOptions object can have the following members:

*bcs*

A Boolean specifying whether boundary conditions are shown. The default value is OFF.

*connectors*

A Boolean specifying whether connectors are shown. The default value is OFF.

*cnxEndPoints*

A Boolean specifying whether the connector end points are shown. This member is applicable only if *connectors*=ON. The default value is ON.

*cnxLocalAxes*

A Boolean specifying whether the connector local coordinate system axes are shown. This member is applicable only if *connectors*=ON. The default value is ON.

*cnxTypeLabels*

A Boolean specifying whether the connector section type labels are shown. This member is applicable only if *connectors*=ON. The default value is ON.

*cnxTagDisplay*

A Boolean specifying whether the tag information is displayed along with the connector section type labels. This member is applicable only if *connectors*=ON and if *cnxTypeLabels*=ON. The default value is OFF.

*constraints*

A Boolean specifying whether constraints are shown. The default value is OFF.

*engineeringFeatures*

A Boolean specifying whether to display engineering features. The default value is OFF.

*geometricRestrictions*

A Boolean specifying whether geometric restrictions are shown. The default value is OFF.

*renderBeamProfiles*

A Boolean specifying whether to render the beam profiles. The default value is OFF.

*beamScaleFactor*

A Float specifying the beam profile scale factor. The beamScaleFactor must be greater than zero. The default value is 1.0.

*predefinedFields*

A Boolean specifying whether fields and initial conditions are shown. The default value is OFF.

*interactions*

A Boolean specifying whether interactions are shown. The default value is OFF.

*loads*

A Boolean specifying whether loads are shown. The default value is OFF.

*mesh*

A Boolean specifying whether the mesh is shown. The default value is OFF.

*optimizationTasks*

A Boolean specifying whether optimization tasks are shown. The default value is OFF.

*stopConditions*

A Boolean specifying whether stop conditions are shown. The default value is OFF.

*renderStyle*

A SymbolicConstant specifying how the image in the viewport is rendered. Possible values are WIREFRAME, HIDDEN, SHADED, and FILLED. The default value is WIREFRAME.

*bcOptions*

A [BCDisplayOptions](pt01ch17pyo02.md) object.

*constraintOptions*

A [ConstraintDisplayOptions](pt01ch17pyo03.md) object.

*displayGroup*

A [DisplayGroup](pt01ch16pyo01.md) object specifying the current display group and referring to an object in the *displayGroups* member of [Session](pt01ch47pyo01.md).

*displayGroupInstances*

A repository of [DisplayGroupInstance](pt01ch16pyo02.md) objects.

*engineeringFeatureOptions*

An [EngineeringFeatureDisplayOptions](pt01ch17pyo04.md) object.

*predefinedFieldOptions*

A [PredefinedFieldDisplayOptions](pt01ch17pyo05.md) object.

*geometricRestrictionOptions*

A [GeometricRestrictionDisplayOptions](pt01ch17pyo07.md) object.

*geometryOptions*

A [GeometryDisplayOptions](pt01ch17pyo06.md) object.

*interactionOptions*

An [InteractionDisplayOptions](pt01ch17pyo10.md) object.

*loadOptions*

A [LoadDisplayOptions](pt01ch17pyo13.md) object.

*meshOptions*

A [MeshDisplayOptions](pt01ch17pyo14.md) object.

*optimizationTaskOptions*

An [OptimizationTaskDisplayOptions](pt01ch17pyo15.md) object.

*stopConditionOptions*

A [StopConditionDisplayOptions](pt01ch17pyo17.md) object.

*symbolOptions*

A [SymbolDisplayOptions](pt01ch17pyo18.md) object.

*visibleInstances*

A tuple of Strings specifying the names of the part instances that are visible in the viewport. The default value is an empty sequence.

*step*

A String specifying the step for which objects are to be displayed. Possible values are any valid step name. The default value is "Initial".




