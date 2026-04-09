# 6.5.1 Pressure load stiffness

### 6.5.1 Pressure load stiffness

**Product: **Abaqus/Standard

In geometrically nonlinear analysis pressure loads are applied on the deformed structure. Hence, the equivalent nodal loads are dependent on the nodal displacements. This dependency leads to additional contributions to the Jacobian in the solution procedure used in Abaqus/Standard. The external virtual work is

![](../graphics/stm_eqn08234.gif)where *A* is the surface on which the pressure is applied; ![](../graphics/stm_eqn00483.gif) is the normal to this surface, pointing into the material; ![](../graphics/stm_eqn01597.gif) is the virtual displacement field; and *p* is the pressure magnitude.
### Pressure load stiffness on a surface in three-dimensional space

The expression ![](../graphics/stm_eqn08235.gif) can be rewritten as follows:

![](../graphics/stm_eqn08236.gif)where ![](../graphics/stm_eqn00117.gif) are the current coordinates of a point on the surface, and the surface parametric coordinates (*g*, *h*) are chosen to give the correct sign to ![](../graphics/stm_eqn00483.gif) through the cross product. The external virtual work is then given by

![](../graphics/stm_eqn08237.gif)and the load stiffness matrix is obtained from

![](../graphics/stm_eqn08238.gif)where, for a solid, ![](../graphics/stm_eqn08239.gif).
### Pressure load stiffness on a surface in two-dimensional space

Now

![](../graphics/stm_eqn08240.gif)where ![](../graphics/stm_eqn08241.gif) is a unit vector out of the plane of the model, *t* is the thickness of the two-dimensional solid (which is assumed to be constant), and the surface parametric coordinate *g* is chosen to give the correct sign to ![](../graphics/stm_eqn00483.gif) through the cross product. The external work is then given by

![](../graphics/stm_eqn08242.gif)and the load stiffness matrix is obtained from

![](../graphics/stm_eqn08243.gif)
### Reference

### Reference

"Distributed loads,"  Section 34.4.3 of the Abaqus Analysis User's Guide