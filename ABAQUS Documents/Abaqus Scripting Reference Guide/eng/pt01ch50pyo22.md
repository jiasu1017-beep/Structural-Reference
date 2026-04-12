# 50.22 StructuralDampingByFrequencyComponent object







A StructuralDampingByFrequencyComponent object is used to define structural damping over a range of frequencies.

**Access**

```
import step
mdb.models[*name*].steps[*name*].structuralDampingByFrequency\
.components[*i*]
```

### 50.22.1 Members

The StructuralDampingByFrequencyComponent object has the following members:

*frequency*

A Float specifying the frequency value in cycles/time.

*factor*

A Float specifying the damping factor, ![](../graphics/ker_eqn00234.gif).




