# 17.16 PartDisplayOptions object







The PartDisplayOptions object stores settings that specify how parts are to be displayed in a particular viewport. The PartDisplayOptions object has no constructor. When you create a new viewport, the settings are copied from the current viewport.

**Access**

```
session.viewports[*name*].layers[*name*].partDisplay
import part
session.viewports[*name*].partDisplay
```

### 17.16.1 setValues(...)

This method modifies the PartDisplayOptions object.

**Required arguments**

None.

**Optional arguments**

*renderStyle*

A SymbolicConstant specifying how the image in the viewport is rendered. Possible values are WIREFRAME, HIDDEN, and SHADED. The default value is WIREFRAME.

*visibleDisplayGroups*

A sequence of [DisplayGroup](pt01ch16pyo01.md) objects specifying the DisplayGroups visible in the viewport. Currently the sequence can contain a maximum of one [DisplayGroup](pt01ch16pyo01.md) object. The default value is an empty sequence.

*engineeringFeatures*

A Boolean specifying whether engineering features are shown. The default value is OFF.

*renderBeamProfiles*

A Boolean specifying whether to render the beam profiles. The default value is OFF.

*beamScaleFactor*

A Float specifying the beam profile scale factor. The beamScaleFactor must be greater than zero. The default value is 1.0.

**Return value**

None

**Exceptions**

RangeError.

### 17.16.2 Members

The PartDisplayOptions object can have the following members:

*engineeringFeatures*

A Boolean specifying whether engineering features are shown. The default value is OFF.

*renderBeamProfiles*

A Boolean specifying whether to render the beam profiles. The default value is OFF.

*beamScaleFactor*

A Float specifying the beam profile scale factor. The beamScaleFactor must be greater than zero. The default value is 1.0.

*mesh*

A Boolean specifying whether the mesh should be displayed.

*renderStyle*

A SymbolicConstant specifying how the image in the viewport is rendered. Possible values are WIREFRAME, HIDDEN, and SHADED. The default value is WIREFRAME.

*displayGroup*

A [DisplayGroup](pt01ch16pyo01.md) object specifying the current display group and referring to an object in the *displayGroups* member of [Session](pt01ch47pyo01.md).

*displayGroupInstances*

A repository of [DisplayGroupInstance](pt01ch16pyo02.md) objects.

*engineeringFeatureOptions*

An [EngineeringFeatureDisplayOptions](pt01ch17pyo04.md) object.

*geometryOptions*

A [GeometryDisplayOptions](pt01ch17pyo06.md) object.

*meshOptions*

A [MeshDisplayOptions](pt01ch17pyo14.md) object.




