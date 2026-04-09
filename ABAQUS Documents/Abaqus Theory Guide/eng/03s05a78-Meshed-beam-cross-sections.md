# 3.5.6 Meshed beam cross-sections

### 3.5.6 Meshed beam cross-sections

**Product: **Abaqus/Standard
### Overview

The beam theory introduced in "Beam element formulation,"  Section 3.5.2, applies to homogeneous beams (made out of a single material) and assumes that the shear center of the beam cross-section is either known or can be easily calculated. However, if the beam cross-section is arbitrarily shaped and/or the beam is made of more than one material layer, finding the cross-section shear center and warping function are no longer trivial tasks. To perform these tasks, the cross-section has to be numerically integrated using a finite element discretization over the two-dimensional cross-section region. The nodal degrees of freedom of the finite element cross-section model represent warping displacements (in general, in and out-of-plane warping degrees of freedom) that allow the shear center and beam torsional stiffness to be determined. Numerical integration of this meshed section also provides the stiffness and inertia statistics: integrated axial stiffness ![](../graphics/stm_eqn03970.gif), integrated bending stiffness ![](../graphics/stm_eqn03971.gif), integrated shear stiffness ![](../graphics/stm_eqn03972.gif), total mass per unit length ![](../graphics/stm_eqn03973.gif), and rotary inertia ![](../graphics/stm_eqn03974.gif).

The warping function and the shear center are derived for shear flexible Timoshenko beams under the following assumptions:

Cross-sections are solid or closed and thin-walled and have a torsional constant that is of the same order of magnitude as the polar moment of inertia of the section. Hence, in the elastic range the warping is small, and it is assumed that warping prevention at the ends can be neglected. The axial warping stresses are assumed to be negligible, but the torsional shear stresses are assumed to be of the same order of magnitude as the stresses due to axial forces and bending moments. In this case the warping is dependent on the twist and can be eliminated as an independent variable, which leads to a considerably simplified formulation. Hence, the theory is based on a solid cross-section with unconstrained warping. Using the notation from "Beam element formulation,"  Section 3.5.2, we assume that ![](../graphics/stm_eqn03680.gif) and the axial strains due to warping can be neglected: ![](../graphics/stm_eqn03751.gif).

Beams can be made out of linear elastic materials either with isotropic properties or orthotropic shear properties defined by two shear moduli ![](../graphics/stm_eqn03975.gif) and ![](../graphics/stm_eqn03976.gif) given in two perpendicular directions. The stress-strain relationship for the elastic orthotropic material in the beam cross-section axis yields

![](../graphics/stm_eqn03977.gif)where ![](../graphics/stm_eqn03978.gif) represents the beam's axial stress, ![](../graphics/stm_eqn03979.gif) and ![](../graphics/stm_eqn03980.gif) represent two shear stresses, and the angle ![](../graphics/stm_eqn00904.gif) is a user-defined material orientation. For the isotropic material properties the above relationship becomes

![](../graphics/stm_eqn03981.gif)

Material fibers are aligned with or perpendicular to the beam axis; hence, in-plane warping can be neglected and the out-of-plane degree of freedom is the only unknown warping value. This assumption can be inaccurate if the beam consists of materials with very different stiffness properties.
### Defining the shear center and warping function

At a given stage in the deformation history of the beam, the position of a material point in the cross-section is given by the expression

![](../graphics/stm_eqn03496.gif) Applying the assumptions made for meshed sections, the expressions for the axial and transverse shear strain components simplify to

![](../graphics/stm_eqn03982.gif)

![](../graphics/stm_eqn03983.gif) Express these strain components relative to the centroid and the shear center strains, respectively, as

![](../graphics/stm_eqn03984.gif)

![](../graphics/stm_eqn03985.gif)where ![](../graphics/stm_eqn03986.gif) is a section centroid, ![](../graphics/stm_eqn03987.gif) is a section shear center, ![](../graphics/stm_eqn03988.gif) is the axial strain at the centroid, and ![](../graphics/stm_eqn03989.gif) is the shear strain at the shear center.

The elastic energy in the beam is

![](../graphics/stm_eqn03990.gif)

Using the strain definitions relative to the section strains at the centroid and the shear center, the elastic energy can be written as

![](../graphics/stm_eqn03991.gif)

Although we assume no warping prevention (i.e., ![](../graphics/stm_eqn03992.gif)), the above energy leads to the following condition that requires the warping function to be orthogonal to the axial and bending energies:

![](../graphics/stm_eqn03993.gif)The cross-section centroid is defined as the point about which the coupling between axial and bending vanishes. Hence, the centroid location follows from

![](../graphics/stm_eqn03994.gif) and

![](../graphics/stm_eqn03995.gif) The shear center is defined as the point about which the coupling between twist and transverse shear vanishes. Hence, the following term is zero in the elastic energy:

![](../graphics/stm_eqn03996.gif)

Let us express the warping function as a sum of three parts: a warping function ![](../graphics/stm_eqn03997.gif) superimposed on the unknown rigid translation ![](../graphics/stm_eqn03998.gif) and rigid rotation about the yet unknown shear center ![](../graphics/stm_eqn03999.gif). This assumption can be written as

![](../graphics/stm_eqn04000.gif) Substituting the above into the expression for elastic energy, using the property of the shear center, and minimizing the energy with respect to the warping function, we get

![](../graphics/stm_eqn04001.gif) This equation is solved numerically over the meshed section and gives the value of ![](../graphics/stm_eqn04002.gif).

Recall that the warping function satisfies the orthogonality condition

![](../graphics/stm_eqn04003.gif)Substituting ![](../graphics/stm_eqn02064.gif), grouping axial and bending terms, and using the centroid definition, we get

![](../graphics/stm_eqn04004.gif) This expression must be true for any value of axial strain ![](../graphics/stm_eqn04005.gif) and curvatures ![](../graphics/stm_eqn04006.gif), so we can write two separate equations that provide constant ![](../graphics/stm_eqn03998.gif) and shear center components ![](../graphics/stm_eqn03987.gif):

![](../graphics/stm_eqn04007.gif)

![](../graphics/stm_eqn04008.gif) Hence,

![](../graphics/stm_eqn04009.gif)

![](../graphics/stm_eqn04010.gif) Finally, the section integrated stiffness properties are defined as

![](../graphics/stm_eqn04011.gif)

![](../graphics/stm_eqn04012.gif)

![](../graphics/stm_eqn04013.gif)

![](../graphics/stm_eqn04014.gif) The integrated inertia properties are

![](../graphics/stm_eqn04015.gif)

![](../graphics/stm_eqn04016.gif) where ![](../graphics/stm_eqn04017.gif) is the center of mass given by the equation

![](../graphics/stm_eqn04018.gif)

We assume elastic section behavior in transverse shear and we neglect the effect at the individual material points (shear strain and stress is averaged over the section). This leads to the following relationships for transverse shear stiffness:

![](../graphics/stm_eqn04019.gif)

![](../graphics/stm_eqn04020.gif)

![](../graphics/stm_eqn04021.gif)

![](../graphics/stm_eqn04022.gif)where *k* equals 1.0 for meshed cross-sections and ![](../graphics/stm_eqn01040.gif) depends on the finite element interpolation.