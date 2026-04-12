# 5.1 Defining a local coordinate system for materials in Eulerian elements







**Product: **Abaqus/Explicit  

**Benefits: **You can now define a local coordinate system for materials in Eulerian elements. Therefore, orientation-based materials can be used with Eulerian elements.

**Description: **In the Eulerian section definition you can now define an orientation for one or more materials in the section. Abaqus/Explicit remaps the material orientation as the material flows through element faces. Anisotropic linear elastic materials, orthotropic linear elastic materials, anisotropic hyperelastic materials, and materials with Hill Plasticity can now be used with Eulerian elements. 
**References: **

**Abaqus Analysis User's Guide**
- ["Eulerian analysis," Section 14.1.1](../usb/usb-link.md#usb-anl-aeuleriananalysis)

**Abaqus Keywords Reference Guide**
- [*EULERIAN SECTION](../key/key-link.md#usb-kws-meulsection)
- [*ORIENTATION](../key/key-link.md#usb-kws-morientation)




