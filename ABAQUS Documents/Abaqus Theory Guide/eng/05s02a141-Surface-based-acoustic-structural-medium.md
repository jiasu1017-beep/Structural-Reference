# 5.2.7 Surface-based acoustic-structural medium interaction

### 5.2.7 Surface-based acoustic-structural medium interaction

**Products: **Abaqus/Standard  Abaqus/Explicit

Abaqus provides two alternatives for modeling interaction between acoustic and structural media: surface-based interaction or acoustic interface (ASIn) elements. Both are available in Abaqus/Standard, but only the surface-based capability is available in Abaqus/Explicit. If the special-purpose interface elements (ASIn) are used, interacting structural and acoustic nodes must be shared by the two meshes. The surface-based capability can be used for structural and acoustic meshes that have different node numbering and whose surface meshes may not be spatially coincident. The ease of use and low computational cost of the surface-based procedure make it preferable to the element-based approach.
### The equations on the contact interface between the structure and the acoustic medium

In the surface-based method the tractions and volumetric acceleration fluxes are computed between structural and acoustic media. In place of consistent distributed tractions or fluxes on both media, one side (identified as the "slave") receives point tractions/fluxes based on interpolation with the shape functions from the other ("master") side. Either the acoustic fluid or the structural solid can be the slave or master, and no Lagrange multipliers are introduced in the formulation. The basis for deciding which to make slave or master is discussed in the Abaqus Analysis User's Guide.

The transient expressions for the coupled acoustic-structural problem are

![](../graphics/stm_eqn07844.gif)(acoustic medium) and

![](../graphics/stm_eqn07845.gif)(structural medium), where ![](../graphics/stm_eqn07846.gif) is the normal vector pointing into the fluid. The fluid-solid surface consists of the union of the directly coupled fluid-solid region, ![](../graphics/stm_eqn07847.gif), and a region coupled via a "reactive" acoustic surface or impedance boundary, ![](../graphics/stm_eqn07848.gif). Of primary interest here are those terms integrated over ![](../graphics/stm_eqn07849.gif), which couple the two variational equations. The fluid impedance integral, over ![](../graphics/stm_eqn07850.gif), depends only on the acoustic pressure field and its variations, so it is unaffected by the contact with the solid. The derivation for the steady-state case is formally identical to the transient case and will not be discussed here. For details of the differences in transient and steady-state acoustics in Abaqus, see "Coupled acoustic-structural medium analysis,"  Section 2.9.1.

When ASIn elements are used (see "Acoustic interface elements,"  Section 32.13.1 of the Abaqus Analysis User's Guide), the formulation requires that the fluid and solid elements be geometrically and nodally conformal so that the shape functions for the structural displacements and the acoustic pressures are identical. The shape functions are integrated using standard methods to yield element matrices of dimension equal to the number of surface nodes on the element. The complete fluid-solid coupling matrices are formed by the sum over the element faces; that is, a standard element assembly operation. The two final coupling matrices have the sparsity pattern of the coupled fluid-solid element faces.

In surface-based coupling the interaction surface ![](../graphics/stm_eqn07851.gif) is formed by the boundary between possibly nonconforming structural and acoustic meshes. Therefore, the fluid-solid coupling matrix cannot be broken up into a sum over element faces as simply as in the ASIn case. To derive the coupling matrices in the surface-based procedure, we use a variation of the master-slave procedure used in small-sliding contact (see "Small-sliding interaction between bodies,"  Section 5.1.1). At the start of an analysis, the projections ![](../graphics/stm_eqn07852.gif) of slave nodes onto the master surface are found, and the areas ![](../graphics/stm_eqn07853.gif) and normals ![](../graphics/stm_eqn07854.gif) associated with the slave nodes are computed. The projections are points ![](../graphics/stm_eqn07855.gif) on the master surface; master nodes in the vicinity of this projection are identified. Variables at the slave nodes ![](../graphics/stm_eqn07852.gif) are then interpolated from variables at the identified master surface nodes near the projection ![](../graphics/stm_eqn07855.gif).

Since the physical degrees of freedom for the fluid and solid meshes are different, two cases must be treated. The two cases handle the discretization of the coupling terms differently.
### Solid/structural master, fluid slave

If the fluid medium surface is designated as the slave, we constrain values at each fluid node to be an average of the values at nearby master surface nodes (see [Figure 5.2.7&#8211;1](05s02a141.md)). The pointwise fluid-solid coupling condition,

![](../graphics/stm_eqn07856.gif)is enforced at the slave nodes, resulting in displacement degrees of freedom added to the fluid slave surface. These slave displacements are constrained by the master displacements and thereby eliminated; the slave pressures are not constrained directly.

Figure 5.2.7&#8211;1 Fluid slave.

![](../graphics/stmstructacouscontact-slave-nls.png)Hence, the fluid equation coupling term

![](../graphics/stm_eqn07857.gif)is equal to

![](../graphics/stm_eqn07858.gif)This term is now approximated, at the slave node level, by the interpolated values of structural displacements at the nearby master nodes times the area of the slave node:

![](../graphics/stm_eqn07859.gif)where ![](../graphics/stm_eqn07860.gif) is the master surface interpolant evaluated at the projection of the slave node, ![](../graphics/stm_eqn07861.gif) are the structural accelerations at the master nodes, and ![](../graphics/stm_eqn07862.gif) is the normal vector, pointing into the fluid, evaluated at the slave node. The summation extends over all master nodes ![](../graphics/stm_eqn07863.gif) in the vicinity of the slave node projection ![](../graphics/stm_eqn07855.gif) (see [Figure 5.2.7&#8211;1](05s02a141.md)). The computation is repeated for each slave node ![](../graphics/stm_eqn07852.gif) on the surface ![](../graphics/stm_eqn07851.gif) and assembled to form the entire coupling matrix.

Similarly, the contribution to the pressure coupling term in the structural equation due to slave node ![](../graphics/stm_eqn07852.gif) is approximated by

![](../graphics/stm_eqn07864.gif)where ![](../graphics/stm_eqn07865.gif) is the acoustic pressure at slave node ![](../graphics/stm_eqn07852.gif), and the sum is again over the master nodes ![](../graphics/stm_eqn07863.gif) in the vicinity of the slave node projection.

These expressions for the coupling terms result in matrices that are the transpose of each other. The normal vectors at the slave surface are used, so these vectors must be well-defined (see "Surfaces: overview,"  Section 2.3.1 of the Abaqus Analysis User's Guide).
### Fluid master, solid/structural slave

If the solid medium is designated as the slave, the values on this surface are constrained to equal values interpolated from the master surface. The pointwise fluid-solid coupling condition is again enforced at the slave nodes, resulting in acoustic pressure degrees of freedom added to the solid slave surface (see [Figure 5.2.7&#8211;2](05s02a141.md)). These slave pressures are constrained by the master surface acoustic pressures and eliminated; the slave displacements are not constrained directly. Hence, the contribution to the coupling term in the acoustic equation for a single slave node ![](../graphics/stm_eqn07852.gif) is approximated by

![](../graphics/stm_eqn07866.gif)where ![](../graphics/stm_eqn07867.gif) is the structural acceleration at the slave node and ![](../graphics/stm_eqn07868.gif) are the interpolants on the fluid (master) surface evaluated at the projection ![](../graphics/stm_eqn07869.gif). The summation extends over the master nodes ![](../graphics/stm_eqn07863.gif) in the vicinity of the slave node projection and is repeated for all solid/structural nodes in the surface ![](../graphics/stm_eqn07851.gif) to compute the entire coupling matrix.

Figure 5.2.7&#8211;2 Fluid master.

![](../graphics/stmstructacouscontact-master-nls.png)

The contribution of a slave node to the coupling term in the structural equation is approximated by

![](../graphics/stm_eqn07870.gif)where ![](../graphics/stm_eqn07871.gif) is the pressure at master node ![](../graphics/stm_eqn07863.gif) and the sum is again over the master nodes in the vicinity of the slave node projection ![](../graphics/stm_eqn07869.gif).
### Reference

### Reference

"Acoustic, shock, and coupled acoustic-structural analysis,"  Section 6.10.1 of the Abaqus Analysis User's Guide