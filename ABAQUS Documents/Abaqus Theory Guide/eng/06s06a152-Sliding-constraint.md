# 6.6.1 Sliding constraint

### 6.6.1 Sliding constraint

**Products: **Abaqus/Standard  Abaqus/Explicit

The sliding constraint has a variety of uses. For example, this MPC is used in conjunction with other MPC types to constrain a shell element mesh to a solid element mesh. The MPC maintains consistency with standard shell theory by forcing initially straight lines through the thickness to remain straight despite rotation and displacement. When applied to solid element nodes on the shell-solid interface, this MPC enforces a kinematic approximation of compatibility with the shell model.

The theory of this constraint is as follows:

Let ![](../graphics/stm_eqn08310.gif), ![](../graphics/stm_eqn08311.gif) be the points defining the line; and let ![](../graphics/stm_eqn08312.gif) be the node that must lie on this line. The direction of the line is given by

![](../graphics/stm_eqn08313.gif)where

![](../graphics/stm_eqn08314.gif)Let ![](../graphics/stm_eqn08315.gif) be base vectors in the *x*-, *y*-, *z*-directions in the global coordinate system. Then, define a unit vector normal to the line as

![](../graphics/stm_eqn08316.gif)unless ![](../graphics/stm_eqn08317.gif), in which case we use

![](../graphics/stm_eqn08318.gif)Now we can define an orthogonal normal as

![](../graphics/stm_eqn08319.gif)![](../graphics/stm_eqn08320.gif), and ![](../graphics/stm_eqn00483.gif) now form a set of orthonormal base vectors with ![](../graphics/stm_eqn04159.gif) and ![](../graphics/stm_eqn04161.gif) normal to the line joining ![](../graphics/stm_eqn08310.gif) and ![](../graphics/stm_eqn08311.gif). The constraint can be imposed by the condition that the line joining the node *m* to node 1 be perpendicular to ![](../graphics/stm_eqn04159.gif) and ![](../graphics/stm_eqn04161.gif); that is,

![](../graphics/stm_eqn08321.gif)and

![](../graphics/stm_eqn08322.gif)We now choose a local coordinate numbering system such that *i* is the global direction on which ![](../graphics/stm_eqn04159.gif) has its largest projection:

![](../graphics/stm_eqn08323.gif)Likewise, we choose global direction *j* such that ![](../graphics/stm_eqn08324.gif) and

![](../graphics/stm_eqn08325.gif)Using this definition of ![](../graphics/stm_eqn08326.gif) the constraint conditions can be written explicitly in terms of coordinate components of node *m* as

![](../graphics/stm_eqn08327.gif)and

![](../graphics/stm_eqn08328.gif)These equations can be used to eliminate ![](../graphics/stm_eqn08329.gif) (note that the numbering of ![](../graphics/stm_eqn08330.gif) avoids dividing through by zero in this elimination):

![](../graphics/stm_eqn08331.gif)and

![](../graphics/stm_eqn08332.gif)

The above equations will enforce the desired constraint. We also need the derivatives of these constraints. These are

![](../graphics/stm_eqn08333.gif)and

![](../graphics/stm_eqn08334.gif)where

![](../graphics/stm_eqn08335.gif)and

![](../graphics/stm_eqn08336.gif)

These equations reduce to

![](../graphics/stm_eqn08337.gif)and

![](../graphics/stm_eqn08338.gif)![](../graphics/stm_eqn08339.gif) can be obtained from the definition of ![](../graphics/stm_eqn00483.gif) to give

![](../graphics/stm_eqn08340.gif)and, therefore,

![](../graphics/stm_eqn08341.gif)and

![](../graphics/stm_eqn08342.gif)The incremental constraint equations become

![](../graphics/stm_eqn08343.gif)and

![](../graphics/stm_eqn08344.gif)Let ![](../graphics/stm_eqn08345.gif). Then, the above equations, when written out in full with the same ordering of ![](../graphics/stm_eqn08346.gif) used above, are

![](../graphics/stm_eqn08347.gif)and

![](../graphics/stm_eqn08348.gif)Solving for ![](../graphics/stm_eqn08349.gif) we obtain

![](../graphics/stm_eqn08350.gif)and

![](../graphics/stm_eqn08351.gif)

In the two-dimensional case ![](../graphics/stm_eqn00483.gif) lies in the *x*&#8211;*y* or *r*&#8211;*z* plane and ![](../graphics/stm_eqn08352.gif). This implies that the second constraint equation is satisfied automatically. The remaining constraint equation is

![](../graphics/stm_eqn08353.gif)and its derivative is

![](../graphics/stm_eqn08354.gif)
### Reference

### Reference

"General multi-point constraints,"  Section 35.2.2 of the Abaqus Analysis User's Guide