# 2.10.1 Piezoelectric analysis

### 2.10.1 Piezoelectric analysis

**Product: **Abaqus/Standard

The piezoelectrical effect is the coupling of stress and electrical field in a material: an electrical field causes the material to strain, and vice versa. Abaqus/Standard has the capability to perform fully coupled piezoelectric analysis. The elements that are used in this case contain both displacement degrees of freedom and the electric potential as nodal variables.
### Equilibrium and flux conservation

The piezoelectric effect is governed by coupled mechanical equilibrium and electric flux conservation equations.

The mechanical equilibrium equation is

![](../graphics/stm_eqn02179.gif)where ![](../graphics/stm_eqn00033.gif) is the "true" (Cauchy) stress at a point currently at ![](../graphics/stm_eqn00117.gif); ![](../graphics/stm_eqn00479.gif) is the traction across a point of the surface of the body; ![](../graphics/stm_eqn00480.gif) is the body force per unit volume in the body (such as the d'Alembert force ![](../graphics/stm_eqn02180.gif), in which ![](../graphics/stm_eqn00593.gif) is the density of the body); and ![](../graphics/stm_eqn02181.gif), where ![](../graphics/stm_eqn01597.gif) is an arbitrary, continuous vector field (the virtual velocity field).

The electrical flux conservation equation is

![](../graphics/stm_eqn02182.gif)where ![](../graphics/stm_eqn00178.gif) is the electric flux vector; ![](../graphics/stm_eqn02183.gif) is the electric flux per unit area entering the body at a point on its surface; ![](../graphics/stm_eqn02184.gif) is the electric flux entering the body per unit volume; and ![](../graphics/stm_eqn02185.gif), where ![](../graphics/stm_eqn02186.gif) is an arbitrary, continuous, scalar field (the virtual potential). These quantities are also known by other terms that are frequently used within electrical engineering references. The electric flux vector *q* is known as the electrical displacement, and the potential gradient *E* is known as the electrical field.
### Constitutive behavior: material coupling

Currently the assumption of linear materials is utilized. The basic equations for a piezoelectric linear medium are defined in the following. Following [Ikeda (1990)](07s01a01-References.md), three alternative forms of the constitutive equations are presented:

*e*-form:

![](../graphics/stm_eqn02187.gif)

![](../graphics/stm_eqn02188.gif)

*d*-form:

![](../graphics/stm_eqn02189.gif)

![](../graphics/stm_eqn02190.gif)

*g*-form:

![](../graphics/stm_eqn02191.gif)

![](../graphics/stm_eqn02192.gif)where ![](../graphics/stm_eqn02193.gif) are the material compliances; ![](../graphics/stm_eqn02194.gif) are the material stiffnesses; ![](../graphics/stm_eqn02195.gif) and ![](../graphics/stm_eqn02196.gif) are piezoelectric constants; and ![](../graphics/stm_eqn02197.gif) are the dielectric constants. In these equations the superscript ![](../graphics/stm_eqn02198.gif), or ![](../graphics/stm_eqn01110.gif) above a particular property indicates that the property is defined at zero electrical gradient, at zero electrical displacement, at zero strain, and at zero stress, respectively. Since all these forms describe the same constitutive relationships, the different mechanical and piezoelectrical constants can be expressed in terms of one another. The following relationships exist among the properties ([Ikeda, 1990](07s01a01-References.md)):

![](../graphics/stm_eqn02199.gif)

![](../graphics/stm_eqn02200.gif)

![](../graphics/stm_eqn02201.gif)

![](../graphics/stm_eqn02202.gif)In Abaqus the constitutive equations in the *e*-form are used:

![](../graphics/stm_eqn02203.gif)

![](../graphics/stm_eqn02204.gif)These are expressed in terms of the piezoelectric stress coefficient matrix ![](../graphics/stm_eqn02205.gif). However, Abaqus also allows the input of piezoelectric constants in terms of the piezoelectric strain coefficient matrix ![](../graphics/stm_eqn02206.gif).

The constitutive equations in the *g*-form can also be expressed as

![](../graphics/stm_eqn02207.gif) and

![](../graphics/stm_eqn02208.gif)These equations can be convenient in interpreting and verifying the results of piezoelectrical analyses.
### Kinematics

For the piezoelectric elements both displacements and electric potentials exist at the nodal locations. The displacements and electrical potentials are approximated within the element as

![](../graphics/stm_eqn02209.gif)and

![](../graphics/stm_eqn02210.gif)where ![](../graphics/stm_eqn02211.gif) is the array of interpolating functions and ![](../graphics/stm_eqn02212.gif) and ![](../graphics/stm_eqn02213.gif) are nodal quantities. The body forces and charges as well as the surface forces and charges are interpolated in a similar manner.

The strains and electrical potential gradients are given as

![](../graphics/stm_eqn02214.gif)and

![](../graphics/stm_eqn02215.gif)where ![](../graphics/stm_eqn02216.gif) and ![](../graphics/stm_eqn02217.gif) are the spatial derivatives of ![](../graphics/stm_eqn02211.gif). In geometrically nonlinear analyses these spatial derivatives are defined in the current configuration.
### System equations

With these approximate fields and the constitutive properties given above, in conjunction with the equilibrium and conservation equations, the following system of equations is derived in terms of nodal quantities:

![](../graphics/stm_eqn02218.gif)and

![](../graphics/stm_eqn02219.gif)where

![](../graphics/stm_eqn02220.gif)is the mass matrix (no inertia terms exist for the electrical flux conservation equation), ![](../graphics/stm_eqn00593.gif) is the mass density,

![](../graphics/stm_eqn02221.gif)is the displacement stiffness matrix,

![](../graphics/stm_eqn02222.gif)is the dielectric "stiffness" matrix,

![](../graphics/stm_eqn02223.gif)is the piezoelectric coupling matrix,

![](../graphics/stm_eqn02224.gif)is the mechanical force vector, and

![](../graphics/stm_eqn02225.gif)is the electrical charge vector. In these expressions the constitutive properties are specified in a matrix form where ![](../graphics/stm_eqn02226.gif) is the mechanical relationship, ![](../graphics/stm_eqn02227.gif) is the electrical relationship, and ![](../graphics/stm_eqn02228.gif) is the piezoelectrical relationship. The "load" vectors include the body, surface, and concentrated quantities, as shown. The unknowns are the nodal displacements and potentials. Once these are determined, the strains and potential gradients can be computed using the expressions given above. The stresses and electrical flux densities are computed by means of constitutive relationships.
### Reference

### Reference

"Piezoelectric analysis,"  Section 6.7.2 of the Abaqus Analysis User's Guide