# 1.4.4 The additive strain rate decomposition

### 1.4.4 The additive strain rate decomposition

**Products: **Abaqus/Standard  Abaqus/Explicit

Many useful materials, such as conventional structural metals, can carry only very small amounts of elastic strain (the elastic modulus is typically two or three orders of magnitude larger than the yield stress). We can take advantage of this behavior to simplify the description of the deformation of such a material. Since the behavior is so common, the assumption that the elastic strains are always small forms the basis of almost all of the inelastic material models provided in Abaqus. This section discusses the description of the deformation for this case.

We begin by assuming that the material has a natural elastic reference state in the sense that, at any time in the deformation, we can imagine isolating the immediate neighborhood of a single point in the material, preventing any further inelastic deformation, removing all external forces from the isolated piece, and allowing the material to unload: the deformation associated with this unloading will then be ![](../graphics/stm_eqn00455.gif), the reverse of the elastic deformation. The deformation between the original reference state and this elastically unloaded state is then the inelastic deformation, ![](../graphics/stm_eqn00456.gif):

![](../graphics/stm_eqn00457.gif)The total deformation can, thus, be decomposed as

![](../graphics/stm_eqn00458.gif)from which we can obtain the velocity gradient with respect to position in the current configuration, ![](../graphics/stm_eqn00459.gif), as

![](../graphics/stm_eqn00460.gif)which we write as

![](../graphics/stm_eqn00461.gif)by defining the elastic and plastic velocity gradients, ![](../graphics/stm_eqn00462.gif) and ![](../graphics/stm_eqn00463.gif), by analogy with the definition of the total velocity gradient.

For the materials of concern here, we now assume that the elastic strains, ![](../graphics/stm_eqn00464.gif), are very small compared to unity. Using this together with the left polar decomposition of the elastic deformation, we can write

![](../graphics/stm_eqn00465.gif)where ![](../graphics/stm_eqn00466.gif), ![](../graphics/stm_eqn00467.gif), and ![](../graphics/stm_eqn00468.gif). We now use this decomposition of ![](../graphics/stm_eqn00469.gif) in [Equation 1.4.4&#8211;2](01s04a07.md) to obtain

![](../graphics/stm_eqn00470.gif)We now define

![](../graphics/stm_eqn00471.gif)where ![](../graphics/stm_eqn00424.gif) and ![](../graphics/stm_eqn00472.gif) denote the symmetric and antisymmetric parts of each velocity gradient, respectively. Using these definitions and neglecting the higher-order term, the velocity gradient can now be expressed as

![](../graphics/stm_eqn00473.gif)Taking the symmetric part of this expression gives

![](../graphics/stm_eqn00474.gif)

We now make the assumption that ![](../graphics/stm_eqn00475.gif), which holds for isotropy; and the last expression reduces to

![](../graphics/stm_eqn00476.gif)where we introduce the notation ![](../graphics/stm_eqn00477.gif). [Equation 1.4.4&#8211;3](01s04a07.md) is the classical "additive rate of deformation decomposition" of plasticity theory---see [Aravas (1991)](07s01a01-References.md) for an example. We see that it derives from the general decomposition ([Equation 1.4.4&#8211;1](01s04a07.md)) when we use the symmetric part of the velocity gradient with respect to current position and when the total elastic strain is always small compared to one. The rate of deformation decomposition is used in this form in almost all the inelastic constitutive models in Abaqus, and it is denoted as ![](../graphics/stm_eqn00478.gif).
### Reference

### Reference

"Inelastic behavior,"  Section 23.1.1 of the Abaqus Analysis User's Guide