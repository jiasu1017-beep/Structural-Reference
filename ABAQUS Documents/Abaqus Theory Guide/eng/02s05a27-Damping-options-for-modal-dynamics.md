# 2.5.4 Damping options for modal dynamics

### 2.5.4 Damping options for modal dynamics

**Product: **Abaqus/Standard

For linear dynamic analysis based on modal superposition, several options are provided in Abaqus/Standard to introduce damping, as follows:
### Critical damping factors

The damping in each eigenmode can be given as a fraction of the critical damping for that mode.

The equation of motion for a one degree of freedom system (one of the eigenmodes of the system) is

![](../graphics/stm_eqn01203.gif)where *m* is the mass, *c* the damping, *k* the stiffness, and *q* the modal amplitude.

The solution is of the form

![](../graphics/stm_eqn01204.gif)where *A* is a constant, and

![](../graphics/stm_eqn01205.gif)

The solution will be oscillatory if the expression under the root sign is negative. Critical damping is defined as the damping that makes this expression zero:

![](../graphics/stm_eqn01206.gif)

If the system is critically damped, after any disturbance the system will return to a static equilibrium state as rapidly as possibly without any oscillation.

Typically, when damping is given as a fraction of critical damping associated with each mode, the values used are in the range of 1% to 10% of critical damping. This method of introducing damping has no physical basis in the finite element model: it is a purely mathematical concept introduced in association with the eigenmodes of the system. Thus, the concept cannot be extended to nonlinear applications where the equations of motion of the system are integrated directly and where the natural frequencies of the system are constantly changing because of nonlinearities.
### Rayleigh damping

Rayleigh damping is defined by a damping matrix formed as a linear combination of the mass and the stiffness matrices:

![](../graphics/stm_eqn01207.gif)

With Rayleigh damping the eigenvectors of the damped system are the same as the eigenvectors of the undamped system. Rayleigh damping can, therefore, be converted into critical damping fractions for each mode: this is the way Rayleigh damping is handled in Abaqus/Standard.

A form of Rayleigh damping is also provided in Abaqus for nonlinear analysis. When the problem is nonlinear the mass damping factor can be used directly: the stiffness damping factor is interpreted as creating viscoelastic behavior in which the viscosity is proportional to the elasticity, which gives exactly the stiffness proportional damping effect defined above for the linear case.
### Composite modal damping

When composite modal damping is used, a damping value is defined for each material as a fraction of critical damping to be associated with that material. These values are converted into a weighted average for each eigenmode, weighted by the mass matrix according to the equation

![](../graphics/stm_eqn01208.gif)where ![](../graphics/stm_eqn01209.gif) is the critical damping ratio used in mode ![](../graphics/stm_eqn00904.gif); ![](../graphics/stm_eqn01210.gif) is the critical damping fraction defined for material *m*; ![](../graphics/stm_eqn01211.gif) is the mass matrix associated with material *m*; ![](../graphics/stm_eqn01212.gif) is the eigenvector of the ![](../graphics/stm_eqn00904.gif)th mode; and ![](../graphics/stm_eqn00973.gif) is the generalized mass associated with the ![](../graphics/stm_eqn00904.gif)th mode (![](../graphics/stm_eqn01213.gif), no sum over ![](../graphics/stm_eqn00904.gif)).
### Structural damping

Structural damping assumes that the damping forces are proportional to the forces caused by stressing of the structure and are opposed to the velocity. This form of damping can be used only if the displacement and velocity are exactly 90 out of phase, which is the case when the excitation is sinusoidal, so structural damping can be used only in steady-state and random response analysis. The damping forces are then

![](../graphics/stm_eqn01214.gif)where ![](../graphics/stm_eqn01215.gif) are the forces caused by stressing of the structure, ![](../graphics/stm_eqn01216.gif) are the damping forces, *s* is the structural damping factor, and ![](../graphics/stm_eqn01217.gif).

Any combination of damping options can be used in an analysis: the effects will be added if several damping definitions are chosen.
### Reference

### Reference

"Material damping,"  Section 26.1.1 of the Abaqus Analysis User's Guide