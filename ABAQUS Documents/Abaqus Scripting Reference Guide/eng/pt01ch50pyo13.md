# 50.13 RayleighDampingByFrequencyComponent object







A RayleighDampingByFrequencyComponent object is used to define Rayleigh damping over a range of frequencies.

**Access**

```
import step
mdb.models[*name*].steps[*name*].rayleighDampingByFrequency.components[*i*]
```

### 50.13.1 Members

The RayleighDampingByFrequencyComponent object has the following members:

*frequency*

A Float specifying the frequency value in cycles/time.

*alpha*

A Float specifying the mass proportional damping, ![](../graphics/ker_eqn00423.gif).

*beta*

A Float specifying the stiffness proportional damping, ![](../graphics/ker_eqn00424.gif).




