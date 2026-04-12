# 40.18 OdbDisplayOptions object







The OdbDisplayOptions object stores the display options associated with an [OdbInstance](pt01ch34pyo15.md) object. This object does not have a constructor. Abaqus creates the OdbDisplayOptions object when an [OdbInstance](pt01ch34pyo15.md) object is created using the display options associated with the current viewport at the time of creation.

**Access**

```
import assembly
session.viewports[*name*].assemblyDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.displayGroupInstances[*name*].odbDisplayOptions
import visualization
session.viewports[*name*].layers[*name*].odbDisplay\
.displayGroupInstances[*name*].odbDisplayOptions
import part
session.viewports[*name*].layers[*name*].partDisplay\
.displayGroupInstances[*name*].odbDisplayOptions
session.viewports[*name*].odbDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions
session.viewports[*name*].partDisplay.displayGroupInstances[*name*]\
.odbDisplayOptions
```

### 40.18.1 Members

The OdbDisplayOptions object has the following members:

*commonOptions*

A [DGCommonOptions](pt01ch40pyo02.md) object.

*superimposeOptions*

A [DGSuperimposeOptions](pt01ch40pyo22.md) object.

*contourOptions*

A [DGContourOptions](pt01ch40pyo03.md) object.

*symbolOptions*

A [DGSymbolOptions](pt01ch40pyo23.md) object.

*materialOrientationOptions*

A [DGOrientationOptions](pt01ch40pyo20.md) object.

*displayBodyOptions*

A [DGDisplayBodyOptions](pt01ch40pyo05.md) object.




