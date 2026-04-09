# 2.16.1 J-integral evaluation

### 2.16.1 J-integral evaluation

**Product: **Abaqus/Standard

The *J*-integral is widely accepted as a fracture mechanics parameter for both linear and nonlinear material response. It is related to the energy release associated with crack growth and is a measure of the intensity of deformation at a notch or crack tip, especially for nonlinear materials. If the material response is linear, it can be related to the stress intensity factors. Because of the importance of the *J*-integral in the assessment of flaws, its accurate numerical evaluation is vital to the practical application of fracture mechanics in design calculations. Abaqus/Standard provides a procedure for such evaluations of the *J*-integral, based on the virtual crack extension/domain integral methods ([Parks, 1977](07s01a01-References.md), and [Shih, Moran, and Nakamura, 1986](07s01a01-References.md)). The method is particularly attractive because it is simple to use, adds little to the cost of the analysis, and provides excellent accuracy, even with rather coarse meshes.
### J-integral in two dimensions

In the context of quasi-static analysis the *J*-integral is defined in two dimensions as

![](../graphics/stm_eqn02596.gif)where ![](../graphics/stm_eqn02597.gif) is a contour beginning on the bottom crack surface and ending on the top surface, as shown in [Figure 2.16.1&#8211;1](02s16a52.md); the limit ![](../graphics/stm_eqn02598.gif) indicates that ![](../graphics/stm_eqn02597.gif) shrinks onto the crack tip; ![](../graphics/stm_eqn02599.gif) is a unit vector in the virtual crack extension direction; and ![](../graphics/stm_eqn02561.gif) is the outward normal to ![](../graphics/stm_eqn02597.gif). ![](../graphics/stm_eqn02600.gif) is given by

![](../graphics/stm_eqn02601.gif) For elastic material behavior *W* is the elastic strain energy; for elastic-plastic or elastic-viscoplastic material behavior *W* is defined as the elastic strain energy density plus the plastic dissipation, thus representing the strain energy in an "equivalent elastic material." This implies that the *J*-integral calculation is suitable only for monotonic loading of elastic-plastic materials.

Figure 2.16.1&#8211;1 Contour for evaluation of the *J*-integral.

![](../graphics/stmjinter-contour-int-path.png)

Following [Shih et al. (1986)](07s01a01-References.md), we rewrite [Equation 2.16.1&#8211;1](02s16a52.md) in the form

![](../graphics/stm_eqn02602.gif)where ![](../graphics/stm_eqn02603.gif) is a sufficiently smooth weighting function within the region enclosed by the closed contour ![](../graphics/stm_eqn02604.gif) and has the value ![](../graphics/stm_eqn02605.gif) on ![](../graphics/stm_eqn02597.gif) and ![](../graphics/stm_eqn02606.gif) on *C*; and ![](../graphics/stm_eqn02607.gif) is the outward normal to the domain enclosed by the closed contour, as shown in [Figure 2.16.1&#8211;2](02s16a52.md). ![](../graphics/stm_eqn02608.gif) on ![](../graphics/stm_eqn02597.gif); and ![](../graphics/stm_eqn02609.gif) is the surface traction on the crack surfaces ![](../graphics/stm_eqn02610.gif) and ![](../graphics/stm_eqn02611.gif).

Figure 2.16.1&#8211;2 Closed contour ![](../graphics/stm_eqn02604.gif) encloses a domain *A* that includes the crack-tip region as ![](../graphics/stm_eqn02612.gif)

![](../graphics/stmjinter-domain-2d.png)

Using the divergence theorem, we convert the closed contour integral into the domain integral

![](../graphics/stm_eqn02613.gif)where *A* is the domain enclosed by the closed contour ![](../graphics/stm_eqn02604.gif). It is worth noting that the domain *A* includes the crack-tip region as ![](../graphics/stm_eqn02598.gif).

If equilibrium is satisfied and *W* is a function of the mechanical strain---i.e., ![](../graphics/stm_eqn02614.gif)---we have

![](../graphics/stm_eqn02615.gif)where ![](../graphics/stm_eqn00480.gif) is the body force per unit volume and ![](../graphics/stm_eqn02616.gif) is the thermal strain. Substituting the above two equations into [Equation 2.16.1&#8211;3](02s16a52.md) gives

![](../graphics/stm_eqn02617.gif)

To evaluate these integrals, Abaqus defines the domain in terms of rings of elements surrounding the crack tip. Different "contours" (domains) are created. The first contour consists of those elements directly connected to crack-tip nodes. The next contour consists of the ring of elements that share nodes with the elements in the first contour as well as the elements in the first contour. Each subsequent contour is defined by adding the next ring of elements that share nodes with the elements in the previous contour. ![](../graphics/stm_eqn02603.gif) is chosen to have a magnitude of zero at the nodes on the outside of the contour and to be one (in the crack direction) at all nodes inside the contour except for the midside nodes (if they exist) in the outer ring of elements. These midside nodes are assigned a value between zero and one according to the position of the node on the side of the element.
### J-integral in three dimensions

The *J*-integral can be extended to three dimensions by considering a crack with a tangentially continuous front, as shown in [Figure 2.16.1&#8211;3](02s16a52.md). The local direction of virtual crack extension is again given by ![](../graphics/stm_eqn02599.gif),

Figure 2.16.1&#8211;3 Definition of local orthogonal Cartesian coordinates at the point *s* on the crack front; the crack is in the ![](../graphics/stm_eqn01412.gif)&#8211;![](../graphics/stm_eqn02618.gif) plane.

![](../graphics/stmjinter-crack-front-nls.png) which is perpendicular to the local crack front and lies in the crack plane. Asymptotically, as ![](../graphics/stm_eqn02619.gif), the conditions for path independence apply on any contour in the ![](../graphics/stm_eqn01412.gif)&#8211;![](../graphics/stm_eqn01413.gif) plane, which is perpendicular to the crack front at *s*. Hence, the *J*-integral defined in this plane can be extended to represent the pointwise energy release rate along the crack front as

![](../graphics/stm_eqn02620.gif)

For a virtual crack advance ![](../graphics/stm_eqn02621.gif) in the plane of a three-dimensional crack, the energy release rate is given by

![](../graphics/stm_eqn02622.gif)where *L* denotes the crack front under consideration; ![](../graphics/stm_eqn02623.gif) is a surface element on a vanishingly small tubular surface enclosing the crack tip (i.e., ![](../graphics/stm_eqn02624.gif)); and ![](../graphics/stm_eqn00483.gif) is the outward normal to ![](../graphics/stm_eqn02623.gif). ![](../graphics/stm_eqn02625.gif) can be calculated by the domain integral method similar to that used in two dimensions. To do so, we first convert the surface integral in [Equation 2.16.1&#8211;6](02s16a52.md) to a volume integral by introducing a contour surface ![](../graphics/stm_eqn02626.gif), outside surface ![](../graphics/stm_eqn02627.gif), external surfaces ![](../graphics/stm_eqn02628.gif) at the ends of the crack front (the surfaces ![](../graphics/stm_eqn02628.gif) vanish for the crack whose front forms a closed loop), and the crack faces ![](../graphics/stm_eqn02629.gif), as shown in [Figure 2.16.1&#8211;4](02s16a52.md).

Figure 2.16.1&#8211;4 Surface ![](../graphics/stm_eqn02630.gif) encloses a domain volume *V* that includes the crack-front region as ![](../graphics/stm_eqn02612.gif)

![](../graphics/stmjinter-domain-3d-nls.png)It can be seen that ![](../graphics/stm_eqn02630.gif) encloses a volume *V*. A weighting function ![](../graphics/stm_eqn02603.gif) is defined such that it has a magnitude of zero on ![](../graphics/stm_eqn02626.gif) and ![](../graphics/stm_eqn02631.gif) on ![](../graphics/stm_eqn02627.gif). ![](../graphics/stm_eqn02603.gif) is assumed to vary smoothly between these values within *A*. On the external surfaces ![](../graphics/stm_eqn02628.gif) where ![](../graphics/stm_eqn02599.gif) is not tangential to the surfaces, it must be made so. This can be done in Abaqus by defining the surface normals explicitly. Then, we can rewrite [Equation 2.16.1&#8211;6](02s16a52.md) as

![](../graphics/stm_eqn02632.gif)where ![](../graphics/stm_eqn02607.gif) is the outward normal to *A* (and ![](../graphics/stm_eqn02608.gif) on ![](../graphics/stm_eqn02627.gif)). ![](../graphics/stm_eqn02609.gif) is the surface traction on surfaces ![](../graphics/stm_eqn02628.gif) and the crack surfaces ![](../graphics/stm_eqn02629.gif).

Using the divergence theorem, we obtain

![](../graphics/stm_eqn02633.gif)

To obtain ![](../graphics/stm_eqn02634.gif) at each node set *P* along the crack front line, ![](../graphics/stm_eqn02621.gif) is discretized with the same interpolation functions as those used in the finite elements along the crack front:

![](../graphics/stm_eqn02635.gif)where ![](../graphics/stm_eqn02636.gif) at the node set *P* and all other ![](../graphics/stm_eqn02637.gif) are zero. This expression for ![](../graphics/stm_eqn02621.gif) is substituted into [Equation 2.16.1&#8211;8](02s16a52.md). Finally, the *J*-integral value at each node set *P* along the crack front can be calculated as

![](../graphics/stm_eqn02638.gif)
### Reference

### Reference

"Contour integral evaluation,"  Section 11.4.2 of the Abaqus Analysis User's Guide