# 4.4 K–epsilon realizable turbulence model in Abaqus/CFD







### 4.4 K--epsilon realizable turbulence model in Abaqus/CFD

**Product: **Abaqus/CFD  

**Benefits: **You can now apply the *k*–![](../graphics/rnb_eqn00001.gif) realizable turbulence model to fluid flow problems.

**Description: **The *k*–![](../graphics/rnb_eqn00001.gif) realizable model is a two-equation turbulence model that evolves an equation for the turbulent kinetic energy, *k*, and the energy dissipation rate, ![](../graphics/rnb_eqn00001.gif). The model equations are developed from fundamental physical principles and dimensional analysis; the equation for *k* is derived using first principles, and the equation for ![](../graphics/rnb_eqn00001.gif) is postulated using physical insight. This particular version uses realizability constraints, which imposes mathematical consistency in the Reynolds stresses (such as enforcing the positivity of the normal stresses and the Cauchy-Schwarz inequality) to modify the model coefficients and the epsilon equation. These modifications guarantee the physical consistency in the predicted Reynolds stresses. To increase the accuracy of the *k*–![](../graphics/rnb_eqn00001.gif) realizable model in cases where the mesh is not fine enough to resolve the viscous sub-layer in wall-bounded flows, a near-wall model, known as the two-layer model, is implemented. 
**References: **

**Abaqus Analysis User's Guide**
- ["Incompressible fluid dynamic analysis," Section 6.6.2](../usb/usb-link.md#usb-anl-aifluiddyn)

**Abaqus Keywords Reference Guide**
- [*TURBULENCE MODEL](../key/key-link.md#usb-kws-hturbulence)




