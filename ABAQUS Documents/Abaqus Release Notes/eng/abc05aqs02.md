# 5.2 Enhancements to the XFEM-based crack propagation capability







**Product: **Abaqus/Standard  

**Benefits: **The extended finite element method (XFEM) allows you to model discontinuities, such as cracks, along an arbitrary, solution-dependent path during an analysis. This method can now be extended to include the pore pressure degrees of freedom to account for the discontinuities of pore pressure as well as the fluid flow within the cracked element surfaces. This capability is very useful to accurately assess the hydraulic fracture process in the oil-gas industry as well as fluid flow in the life science and consumer goods industries. To improve the accuracy, you can now use nonlocal averaging stress and strain fields to determine if the damage initiation criterion is satisfied and to determine the crack propagation direction. In addition, output of some quantities on the cracked element surfaces is supported.

**Description: **XFEM allows you to model crack growth without remeshing the crack surfaces since it does not require the mesh to match the geometry of the crack. The XFEM-based cohesive segments method is extended to model hydraulically driven fracture. In this case additional phantom nodes with pore pressure degrees of freedom are introduced to model the fluid flow within the cracked element surfaces and to represent the discontinuities of displacement and fluid pressure in a cracked element. The fluid flow continuity, which accounts for both tangential and normal flow within and across the cracked element surfaces as well as the rate of opening of the cracked element surfaces, is maintained. The fluid pressure on the cracked element surfaces contributes to the traction-separation behavior of the cohesive segments in the enriched elements, which enables the modeling of hydraulically driven fracture. 

In previous releases you could use the local stress and strain fields of an element ahead of the crack tip to determine the crack propagation and if the fracture criterion was satisfied. In the case of coarse and/or unstructured meshes a nonlocal averaging of the stress and strain fields ahead of the crack tip can lead to a more accurate evaluation of those fields, which can improve the accuracy of the computed propagation directions.

You can now output and visualize some surface variables on the cracked element surfaces.
**References: **

**Abaqus Analysis User's Guide**
- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1](../usb/usb-link.md#usb-anl-aenrichment)
- ["Boundary conditions in Abaqus/Standard and Abaqus/Explicit," Section 34.3.1](../usb/usb-link.md#usb-prc-pboundary)
- ["Pore fluid flow," Section 34.4.7](../usb/usb-link.md#usb-prc-pporousflow)

**Abaqus Keywords Reference Guide**
- [*BOUNDARY](../key/key-link.md#usb-kws-hboundary)
- [*CFLOW](../key/key-link.md#usb-kws-hcflow)
- [*CONTACT OUTPUT](../key/key-link.md#usb-kws-hcontactoutput)
- [*DAMAGE INITIATION](../key/key-link.md#usb-kws-mdamageinitiation)
- [*ENRICHMENT](../key/key-link.md#usb-kws-menrichment)

**Abaqus Benchmarks Guide**
- ["Propagation of hydraulically driven fracture using XFEM," Section 1.19.5](../bmk/bmk-link.md#bmk-anl-xfemhydrfract)




