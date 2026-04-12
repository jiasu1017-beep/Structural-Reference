# 12.2 Output of mode mix ratios during mixed mode delamination







**Product: **Abaqus/Standard  

**Benefits: **For delamination behavior modeled with cohesive elements, you can now output the mode mix ratios both at the initiation of damage and during damage evolution.

**Description: **Delamination is a common failure mode for laminated composite materials, and the energy required for delamination is generally a strong function of the mode mix ratio in the delamination zone. The mode mix ratio refers to the relative proportion of tensile to shear deformation. In most practical situations, the delamination process is strongly mixed mode in nature, and the mode mix ratio often varies significantly during the delamination process. The new output variables, MMIXDMI and MMIXDME, measure the mode mix ratios at integration points in cohesive elements at damage initiation and during damage evolution, respectively. These variables provides an accurate measure of the mode of failure (tensile versus shear) during mixed mode delamination.
**References: **

**Abaqus Analysis User's Guide**
- ["Defining the constitutive response of cohesive elements using a traction-separation description," Section 32.5.6](../usb/usb-link.md#usb-elm-ecohesivebehavior)

**Abaqus Keywords Reference Guide**
- [*OUTPUT](../key/key-link.md#usb-kws-houtput)

**Abaqus Verification Guide**
- ["Transferring results from one Abaqus/Standard analysis to another Abaqus/Standard analysis," Section 3.14.2](../ver/ver-link.md#ver-prc-import-stdtostd)




