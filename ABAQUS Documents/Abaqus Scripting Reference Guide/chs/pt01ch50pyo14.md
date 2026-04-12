# 50.14 RayleighDampingComponent object







A RayleighDampingComponent object is used to define Rayleigh damping over a range of modes.

**Access**

```
import step
mdb.models[*name*].steps[*name*].rayleighDamping.components[*i*]
```

### 50.14.1 Members

The RayleighDampingComponent object has the following members:

*start*

An Int specifying the mode number of the lowest mode of a range.

*end*

An Int specifying the mode number of the highest mode of a range.

*alpha*

A Float specifying the mass proportional damping, ![](../graphics/ker_eqn00423.gif).

*beta*

A Float specifying the stiffness proportional damping, ![](../graphics/ker_eqn00424.gif).




