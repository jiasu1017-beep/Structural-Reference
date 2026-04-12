# 17.15 OptimizationTaskDisplayOptions object







The OptimizationTaskDisplayOptions object stores settings that specify how assemblies are to be displayed in a particular viewport when 

```
session.viewports[*name*].assemblyDisplay.optimizationTasks=ON
```
 The OptimizationTaskDisplayOptions object has no constructor. When you create a new viewport, the settings are copied from the current viewport.

**Access**

```
session.viewports[*name*].assemblyDisplay.optimizationTaskOptions
session.viewports[*name*].layers[*name*].assemblyDisplay\
.optimizationTaskOptions
```

### 17.15.1 setValues(...)

This method modifies the OptimizationTaskDisplayOptions object.

**Required arguments**

None.

**Optional arguments**

*topologyTask*

A Boolean specifying whether topology task symbols are shown. The default value is ON.

*shapeTask*

A Boolean specifying whether shape task symbols are shown. The default value is ON.

**Return value**

None

**Exceptions**

RangeError.

### 17.15.2 Members

The OptimizationTaskDisplayOptions object has members with the same names and descriptions as the arguments to the [setValues](pt01ch17pyo15.md#ker-optimizationtaskdisplayoptions-setvalues-pyc) method.




