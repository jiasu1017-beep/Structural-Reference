# 3.3.1 Solid infinite elements

### 3.3.1 Solid infinite elements

**Products: **Abaqus/Standard  Abaqus/Explicit

The stress analyst is often faced with problems defined in unbounded domains or problems in which the region of interest is small compared with the surrounding medium. The unbounded or infinite medium can be approximated by extending the finite element mesh to a far distance, where the influence of the surrounding medium on the region of interest is considered small enough to be neglected. This approach calls for experimentation with mesh sizes and assumed boundary conditions at the truncated edges of the mesh and is not always reliable. It is particularly of concern in dynamic analysis, when the boundary of the mesh may reflect energy back into the region being modeled. A better approach is to use "infinite elements": elements defined over semi-infinite domains with suitably chosen decay functions. Abaqus provides first- and second-order infinite elements that are based on the work of [Zienkiewicz et al. (1983)](07s01a01-References.md) for static response and of [Lysmer and Kuhlemeyer (1969)](07s01a01-References.md) for dynamic response. The elements are used in conjunction with standard finite elements, which model the area around the region of interest, with the infinite elements modeling the far-field region.
### Static analysis

The solution in the far field is assumed to be linear, so only linear behavior is provided in the infinite elements. The static behavior of the infinite elements is based on modeling the basic solution variable, *u* (in stress analysis *u* is a displacement component) with respect to spatial distance *r* measured from a "pole" of the solution, so that ![](../graphics/stm_eqn03274.gif) as ![](../graphics/stm_eqn03275.gif), and ![](../graphics/stm_eqn03276.gif) as ![](../graphics/stm_eqn01414.gif). The interpolation provides terms of order ![](../graphics/stm_eqn03277.gif), ![](../graphics/stm_eqn03278.gif), and, when the solution variable is a stress-like variable (such as the pore liquid pressure in the analysis of flow through a porous medium), ![](../graphics/stm_eqn03279.gif) as ![](../graphics/stm_eqn01414.gif). The far-field behavior of many common cases, such as a point load on a half-space, is thereby included. This modeling is achieved by using standard quadratic or cubic interpolation for ![](../graphics/stm_eqn03280.gif) in ![](../graphics/stm_eqn03281.gif), where *s* is a mapped coordinate that is chosen such that the mapping ![](../graphics/stm_eqn03282.gif) causes ![](../graphics/stm_eqn03275.gif) as ![](../graphics/stm_eqn03283.gif). We obtain two- and three-dimensional models of domains that reach to infinity by combining this interpolation in the *s*-direction in a product form with standard linear or quadratic interpolation in orthogonal directions in the mapped space.

In using infinite elements for static analysis, the pole must be located so as to provide a reasonable far-field solution for the particular problem being modeled. The infinite elements in Abaqus are written with nodes on the interface between the finite and infinite elements and, on each edge that stretches to infinity, a node that must be placed in the infinite direction such that the straight line from that node through the corresponding interface node passes through the pole for that ray at a distance on the other side of the interface from the infinite element equal to the distance between these nodes ([Figure 3.3.1&#8211;1](03s03a68-Solid-infinite-elements.md)).

Figure 3.3.1&#8211;1 Pole node location for an infinite element.

![](../graphics/stminf-pole-node.png)

The one-dimensional concept is, thus, based on a node (node 1) on the interface between the finite and infinite elements, distance ![](../graphics/stm_eqn03284.gif) from the pole and at ![](../graphics/stm_eqn03285.gif) in the mapped space, and node 2, at ![](../graphics/stm_eqn03286.gif) from the pole (the pole is at ![](../graphics/stm_eqn01415.gif)) and at ![](../graphics/stm_eqn03287.gif) is the mapped space. The ![](../graphics/stm_eqn03282.gif) mapping is chosen as

![](../graphics/stm_eqn03288.gif)so that

![](../graphics/stm_eqn03289.gif)which inverts to give

![](../graphics/stm_eqn03290.gif)

When an element with ![](../graphics/stm_eqn03277.gif) and ![](../graphics/stm_eqn03278.gif) behavior is required, we combine this geometric mapping with standard quadratic interpolation of *u* with respect to *s*, written in terms of its values at node 1 and at node 2:

![](../graphics/stm_eqn03291.gif)(this gives ![](../graphics/stm_eqn03292.gif) at ![](../graphics/stm_eqn03293.gif), where ![](../graphics/stm_eqn03275.gif)). Using the inverted geometric mapping to define ![](../graphics/stm_eqn03294.gif) then gives

![](../graphics/stm_eqn03295.gif)which provides the desired behavior. Likewise, when ![](../graphics/stm_eqn03279.gif) behavior is also required, we use cubic interpolation of *u* with respect to *s*, written in terms of its values at nodes 1 and 2 and at a third node, which we choose to place at ![](../graphics/stm_eqn03296.gif):

![](../graphics/stm_eqn03297.gif)The inverted geometric mapping then provides

![](../graphics/stm_eqn03298.gif)The infinite elements in Abaqus consist of two- and three-dimensional elements for uncoupled stress analysis that use quadratic interpolation for displacement components and two- and three-dimensional elements for coupled stress-pore liquid pressure elements, in which the displacements use quadratic interpolation and the pore liquid pressure uses cubic interpolation in the infinite direction. This higher-order interpolation is used for the pore liquid pressure for compatibility: since the displacement varies as ![](../graphics/stm_eqn03278.gif), the strain (and, therefore, the stress) may vary as ![](../graphics/stm_eqn03279.gif).
### Dynamic response

The dynamic response of the infinite elements is based on consideration of plane body waves traveling orthogonally to the boundary. Again, we assume the response adjacent to the boundary is of small enough amplitude so that the medium responds in a linear elastic fashion.

The equilibrium equation is

![](../graphics/stm_eqn03299.gif)where ![](../graphics/stm_eqn00593.gif) is the material's density, ![](../graphics/stm_eqn00890.gif) is the material particle acceleration, ![](../graphics/stm_eqn00033.gif) is the stress, and ![](../graphics/stm_eqn00117.gif) is position.

We assume the material's response is isotropic, linear elastic, and---thus---can be written as

![](../graphics/stm_eqn03300.gif)where ![](../graphics/stm_eqn00399.gif) is the strain and

![](../graphics/stm_eqn03301.gif)and

![](../graphics/stm_eqn03302.gif)are Lam's constants (*E* is Young's modulus and ![](../graphics/stm_eqn01854.gif) is Poisson's ratio). Introducing this material response in the equilibrium equation, and assuming small strain:

![](../graphics/stm_eqn03303.gif)provides the governing equation for the motion

![](../graphics/stm_eqn03304.gif)where index notation has been used for simplicity.

We consider plane waves traveling along the *x*-axis. Two body wave solutions of this form exist for this equation. One describes plane, longitudinal ("push") waves, which have the form

![](../graphics/stm_eqn03305.gif)where, by substitution in the governing equation above, we find that the wave speed, ![](../graphics/stm_eqn03306.gif), is

![](../graphics/stm_eqn03307.gif)The other solution of this form is the "shear" wave solution

![](../graphics/stm_eqn03308.gif)or

![](../graphics/stm_eqn03309.gif)where---again by substitution in the governing equation---we obtain

![](../graphics/stm_eqn03310.gif)In each case the solution ![](../graphics/stm_eqn03311.gif) represents waves moving in the direction of increasing *x*, while ![](../graphics/stm_eqn03312.gif) represents waves moving in the direction of decreasing *x*.

Now consider a boundary at ![](../graphics/stm_eqn03313.gif) of a medium modeled by finite elements in ![](../graphics/stm_eqn03314.gif). We introduce distributed damping on this boundary, such that

![](../graphics/stm_eqn03315.gif)and

![](../graphics/stm_eqn03316.gif)where we will now choose the damping constants ![](../graphics/stm_eqn03317.gif) and ![](../graphics/stm_eqn03318.gif) to avoid reflection of longitudinal and shear wave energy back into the medium in ![](../graphics/stm_eqn03314.gif). Plane, longitudinal waves approaching the boundary have the form ![](../graphics/stm_eqn03319.gif), ![](../graphics/stm_eqn03320.gif). If they are reflected at all as plane, longitudinal waves, their reflection will travel away from the boundary in some form ![](../graphics/stm_eqn03321.gif), ![](../graphics/stm_eqn03320.gif). Since the problem is linear, superposition provides the total displacement ![](../graphics/stm_eqn03322.gif), with corresponding stresses ![](../graphics/stm_eqn03323.gif), all other ![](../graphics/stm_eqn00540.gif), and velocity ![](../graphics/stm_eqn03324.gif). For this solution to satisfy the damping behavior introduced on the boundary at ![](../graphics/stm_eqn03313.gif) requires

![](../graphics/stm_eqn03325.gif)We can, therefore, ensure that ![](../graphics/stm_eqn03326.gif) (so that ![](../graphics/stm_eqn03327.gif)) for any ![](../graphics/stm_eqn03328.gif) by choosing

![](../graphics/stm_eqn03329.gif)A similar argument for shear waves provides

![](../graphics/stm_eqn03330.gif)

These values of boundary damping are built into the infinite elements in Abaqus. From the above discussion we see that they transmit all normally impinging plane body waves exactly (provided that the material behavior close to the boundary is linear elastic). General problems involve nonplane body waves that do not impinge on the boundary from an orthogonal direction and may also involve Rayleigh surface waves and Love waves. Nevertheless, these "quiet" boundaries work quite well even for such general cases, provided that they are arranged so that the dominant direction of wave propagation is orthogonal to the boundary or, at free surfaces and interfaces where Rayleigh or Love waves are of concern, they are orthogonal to the surface (see, for example, [Cohen and Jennings, 1983](07s01a01-References.md)). As the boundaries are "quiet" rather than silent (perfect transmitters of all waveforms), and because the boundaries rely on the solution adjacent to them being linear elastic, they should be placed some reasonable distance from the region of main interest.

During dynamic response analysis following static preload (as is common in geotechnical applications), the traction provided by the infinite elements to the boundary of the finite element mesh consists of the constant stress obtained from the static response with the quiet boundary damping stress added. Since the elements have no stiffness during dynamic analysis, they allow a net rigid body motion to occur, which is usually not a significant effect.
### Reference

### Reference

"Infinite elements,"  Section 28.3.1 of the Abaqus Analysis User's Guide