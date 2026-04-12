# 44.5 PlyStackPlot object







The PlyStackPlot object is used to plot the stacking of plies in a composite layup or in a composite shell section. 

**Access**

```
import section
import visualization
```

### 44.5.1 MdbPlyStackPlot(...)

This method creates a PlyStackPlot object from a region of a part that contains a composite shell layup.

**Path**

```
section.MdbPlyStackPlot
```

**Required arguments**

*part*

A [Part](pt01ch37pyo01.md) object.

*region*

A [Region](pt01ch45pyo03.md) object which contains a composite shell layup.

**Optional arguments**

None.

**Return value**

A PlyStackPlot object.

**Exceptions**

None.

### 44.5.2 OdbPlyStackPlot(...)

This method creates a PlyStackPlot object from a composite shell section of an Odb object.

**Path**

```
visualization.OdbPlyStackPlot
```

**Required arguments**

*odb*

An [Odb](pt01ch34pyo01.md) object.

*sectionName*

A String specifying the section name that contains a composite shell section.

**Optional argument**

*offset*

A Float specifying the shell offset. The default value is 0.0. 

**Return value**

A PlyStackPlot object.

**Exceptions**

None.

### 44.5.3 Members

The PlyStackPlot object has no members.




