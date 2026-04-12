# 40.27 MdbData object







The MdbData object has no constructor. Abaqus creates an MdbData object when a cae file is opened or a new model is created. There is one MdbData for each model in session. MdbData is updated when it is displayed in a viewport.

**Access**

```
import visualization
session.mdbData[*name*]
```

### 40.27.1 Members

The MdbData object has the following members:

*stepPeriods*

A tuple of (String, Float) tuples specifying the stepName and the stepPeriod.

*steps*

A repository of [MdbDataStep](pt01ch40pyo30.md) objects specifying the list of steps. The repository is read-only.

*instances*

A repository of [MdbDataInstance](pt01ch40pyo29.md) objects specifying the list of instances. The repository is read-only.




