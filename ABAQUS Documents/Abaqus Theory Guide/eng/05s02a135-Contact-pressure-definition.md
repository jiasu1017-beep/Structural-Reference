# 5.2.1 Contact pressure definition

### 5.2.1 Contact pressure definition

**Products: **Abaqus/Standard  Abaqus/Explicit

The contact modeling capabilities in Abaqus allow access to a library of "surface constitutive models." Part of this library in Abaqus/Standard is the definition of the contact pressure between two surfaces at a point, ![](../graphics/stm_eqn02386.gif), as a function of the "overclosure," ![](../graphics/stm_eqn07404.gif), of the surfaces (the interpenetration of the surfaces). Two models for ![](../graphics/stm_eqn07609.gif) are provided as described below.
### Hard contact

In this case

![](../graphics/stm_eqn07610.gif)

The contact constraint is enforced with a Lagrange multiplier representing the contact pressure in a mixed formulation. The virtual work contribution is

![](../graphics/stm_eqn07611.gif)and the linearized form of the contribution is

![](../graphics/stm_eqn07612.gif)
### Softened contact defined with an exponential pressure-overclosure relationship

This model provides an exponential ![](../graphics/stm_eqn02386.gif)&#8211;![](../graphics/stm_eqn07404.gif) relationship, as shown in [Figure 5.2.1&#8211;1](05s02a135.md).

Figure 5.2.1&#8211;1 "Softened" pressure-overclosure relationship using an exponential law.

![](../graphics/ksurfacebehavior-soft-nls.png)

The user defines an initial contact distance, ![](../graphics/stm_eqn07566.gif), and a typical pressure value, ![](../graphics/stm_eqn07613.gif), which is the pressure value at zero overclosure (![](../graphics/stm_eqn07418.gif)). Then, we define |  | for , |
| --- | --- |
|  | for , | and |  | for , |
| --- | --- |
|  | for . | To avoid numerical difficulties at high penetration (![](../graphics/stm_eqn07620.gif)), a linearized pressure-overclosure relation with continuous slope is used.
### Softened contact defined with a tabular pressure-overclosure relationship

The pressure-overclosure (![](../graphics/stm_eqn02386.gif)-![](../graphics/stm_eqn07404.gif)) relationship can be entered directly in tabular form as shown in [Figure 5.2.1&#8211;2](05s02a135.md).

Figure 5.2.1&#8211;2 "Softened" pressure-overclosure relationship defined in tabular form.

![](../graphics/ksurfacebehavior-soft1-nls.png)
### Softened contact defined with a linear pressure-overclosure relationship

The linear pressure-overclosure relationship is similar to the tabular relationship except that the linear form requires only a single value to be input to define the slope and the curve always passes through the origin.
### Softened contact implementation

A mixed formulation is used because the exponential stiffness associated with softened contact tends to slow down convergence or, due to the development of excessive contact stresses, may cause divergence. For the mixed formulation the virtual work contribution is

![](../graphics/stm_eqn07621.gif)where ![](../graphics/stm_eqn02386.gif) is the contact pressure, ![](../graphics/stm_eqn07404.gif) is the actual overclosure, and ![](../graphics/stm_eqn07622.gif) is the overclosure associated with the contact pressure, ![](../graphics/stm_eqn02386.gif). A local Newton loop is used to calculate ![](../graphics/stm_eqn07623.gif) for the current value of ![](../graphics/stm_eqn02386.gif). The linearized form of this contribution is

![](../graphics/stm_eqn07624.gif)where ![](../graphics/stm_eqn07625.gif) is evaluated for the overclosure ![](../graphics/stm_eqn07623.gif). Since there is no term involving ![](../graphics/stm_eqn07626.gif), there is a zero on the diagonal of the Jacobian. A zero on the diagonal is not desirable because it may lead to equation solver problems if a rigid body mode is constrained only by contact elements. Hence, a small reference stiffness ![](../graphics/stm_eqn06810.gif) is introduced by splitting the contact pressure as follows:

![](../graphics/stm_eqn07627.gif)where ![](../graphics/stm_eqn02389.gif) is a Lagrange multiplier and ![](../graphics/stm_eqn06810.gif) is a small reference stiffness (see [Figure 5.2.1&#8211;1](05s02a135.md)):

![](../graphics/stm_eqn07628.gif)

Substituting for the pressure ![](../graphics/stm_eqn02386.gif) in [Equation 5.2.1&#8211;1](05s02a135.md) and [Equation 5.2.1&#8211;2](05s02a135.md), we obtain

![](../graphics/stm_eqn07629.gif)and

![](../graphics/stm_eqn07630.gif)Further,

![](../graphics/stm_eqn07631.gif)Therefore, substituting for ![](../graphics/stm_eqn07632.gif) in [Equation 5.2.1&#8211;4](05s02a135.md),

![](../graphics/stm_eqn07633.gif)Thus, the corresponding system of equations in matrix form is

![](../graphics/stm_eqn07634.gif)

In the mixed formulation the difference between the actual and the calculated overclosure ![](../graphics/stm_eqn07635.gif) will go to zero as part of the iterative solution process. The difference must be sufficiently small to obtain an accurate solution. The admissible error in ![](../graphics/stm_eqn07635.gif) is set to ![](../graphics/stm_eqn07636.gif) for ![](../graphics/stm_eqn07637.gif). For ![](../graphics/stm_eqn07638.gif) the admissible error is interpolated linearly between ![](../graphics/stm_eqn07636.gif) and ![](../graphics/stm_eqn07639.gif), where ![](../graphics/stm_eqn07639.gif) represents the tolerance level at ![](../graphics/stm_eqn07640.gif); alternatively, the tolerances can be specified by the user as part of the solution controls.
### Viscous damping option

In addition to the surface constitutive models described above, where the contact pressure is a function of the surface overclosure, Abaqus/Standard allows for the definition of a "viscous" pressure that is proportional to the relative velocity, ![](../graphics/stm_eqn07641.gif), at which the surfaces approach or separate from each other. This option is intended for the regularization of snap-through problems involving contact where convergence difficulties arise due to the sudden violation of contact constraints.

The damping pressure, ![](../graphics/stm_eqn07642.gif), is given by

![](../graphics/stm_eqn07643.gif)where ![](../graphics/stm_eqn01087.gif) is the damping coefficient. This coefficient is specified as a function of the overclosure, ![](../graphics/stm_eqn07404.gif), as follows:

![](../graphics/stm_eqn07644.gif)where ![](../graphics/stm_eqn06808.gif) is the value of the damping coefficient at zero overclosure and ![](../graphics/stm_eqn02098.gif) is the fraction of the overclosure interval ![](../graphics/stm_eqn07645.gif) over which the damping coefficient is equal to ![](../graphics/stm_eqn06808.gif).

The virtual work contribution associated with the damping pressure is

![](../graphics/stm_eqn07646.gif)The contribution to the stiffness matrix for the Newton solution is given by the linearized form of the virtual work contribution:

![](../graphics/stm_eqn07647.gif)where

![](../graphics/stm_eqn07648.gif)

In static analysis the velocity is defined as the displacement increment divided by the time increment. Therefore, ![](../graphics/stm_eqn07649.gif), and the stiffness contribution reduces to

![](../graphics/stm_eqn07650.gif)

The previous expression also applies to dynamics if the backward Euler time integration operator is used. In the case of dynamics with the Hilber-Hughes-Taylor time integration operator, the stiffness contribution can be written as

![](../graphics/stm_eqn07651.gif)where ![](../graphics/stm_eqn01256.gif) and ![](../graphics/stm_eqn01219.gif) are the Hilber-Hughes-Taylor time integration operator parameters. The viscous damping option cannot be used in a Riks analysis since velocity is not defined.
### Reference

### Reference

"Contact pressure-overclosure relationships,"  Section 37.1.2 of the Abaqus Analysis User's Guide