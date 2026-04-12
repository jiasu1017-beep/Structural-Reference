# 8.2 Enhancements for prescribed conditions in Abaqus/CFD







**Product: **Abaqus/CFD  

**Benefits: **The process to specify initial conditions and boundary conditions for the turbulence model variables is enhanced to be more intuitive and flexible. 

**Description: **You can now specify more intuitive turbulence quantities, such as the turbulence intensity or the turbulent viscosity ratio, and Abaqus/CFD calculates the actual values of the turbulence model variables. Previously, you were required to precompute values for the turbulence variables. The new turbulence quantities can be used to specify initial conditions and boundary conditions for all of the turbulence models. For example, you can prescribe the turbulence intensity ![](../graphics/rnb_eqn00003.gif) and a characteristic velocity scale ![](../graphics/rnb_eqn00004.gif) to specify the turbulent kinetic energy for the *k*–![](../graphics/rnb_eqn00001.gif) RNG, *k*–![](../graphics/rnb_eqn00001.gif) realizable, and *k*–![](../graphics/rnb_eqn00005.gif) SST turbulence models as

![](../graphics/rnb_eqn00006.gif)

**References: **

**Abaqus Analysis User's Guide**
- ["Initial conditions in Abaqus/CFD," Section 34.2.2](../usb/usb-link.md#usb-prc-pinitialcondcfd)
- ["Boundary conditions in Abaqus/CFD," Section 34.3.2](../usb/usb-link.md#usb-prc-pboundarycfd)

**Abaqus Keywords Reference Guide**
- [*FLUID BOUNDARY](../key/key-link.md#usb-kws-hfluidboundary)
- [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond)




