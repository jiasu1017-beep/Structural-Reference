# 34.4 BeamOrientation object







The BeamOrientation object represents the direction of the first beam section axis ![](../graphics/ker_eqn00406.gif). Specifying the beam orientation using an additional node in the element connectivity list is not supported.

**Access**

```
import odbAccess
session.odbs[*name*].parts[*name*].beamOrientations[*i*]
session.odbs[*name*].rootAssembly.instances[*name*].beamOrientations[*i*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.beamOrientations[*i*]
```

### 34.4.1 Members

The BeamOrientation object can have the following members:

*method*

A SymbolicConstant specifying the orientation assignment method. Possible values are N1_COSINES, CSYS, and VECT.

*region*

An [OdbSet](pt01ch34pyo23.md) object specifying a region for which the beam orientation is defined.

*vector*

A tuple of Floats specifying direction cosines of the ![](../graphics/ker_eqn00406.gif)-direction of the beam cross-section.




