# 16.3 DisplayGroupInstanceRepository object







The DisplayGroupInstanceRepository object stores [DisplayGroupInstance](pt01ch16pyo02.md) objects. In addition to all the standard Python repository methods, the [DisplayGroupInstance](pt01ch16pyo02.md) repository defines additional methods as described below.

**Access**

```
import visualization
session.viewports[*name*].layers[*name*].odbDisplay.displayGroupInstances
session.viewports[*name*].odbDisplay.displayGroupInstances
```

### 16.3.1 syncOptions(...)

This method synchronizes the display options stored on the [OdbDisplay](pt01ch35pyo01.md) object with the display options stored on the [DisplayGroupInstance](pt01ch16pyo02.md) object.

**Required argument**

*name*

A String specifying the repository key.

**Optional argument**

*updateInstances*

A Boolean specifying whether to synchronize the display options on all the [DisplayGroupInstance](pt01ch16pyo02.md) objects stored in the DisplayGroupInstanceRepository for which *lockOptions* is OFF. The default value of *updateInstances* is ON.

**Return value**

None

**Exceptions**

None.

### 16.3.2 Members

The DisplayGroupInstanceRepository object has no members.




