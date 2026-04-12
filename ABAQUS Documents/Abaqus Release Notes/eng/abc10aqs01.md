# 10.1 Edge-to-edge contact for general contact in Abaqus/Standard







**Product: **Abaqus/Standard  

**Benefits: **Edge-to-edge contact is extended to include feature edges on solid and shell-like surfaces and shell perimeter edges for more automated and robust resolution of contact between edges. New contact output variables allow visualizing contact enforcement with edge-to-edge contact. 

**Description: **    Feature edges on solid and shell-like surfaces and shell perimeter edges can now participate in edge-to-edge contact within the general contact framework. These changes vastly expand the edge-to-edge contact capability compared to the previous release, where only contact between edges on beam surfaces (beam-to-beam contact) was supported. Various robustness and accuracy improvements have also been made. While edge-to-edge contact is the primary formulation for contact between beams, in other cases (for example, between feature edges), it supplements the edge-to-surface and the surface-to-surface contact when those formulations are active. 

New surface nodal output variables, CLINELOAD and CPOINTLOAD, are provided to visualize contact loads in active contact regions involving edges. Output variable CLINELOAD has units of force per length and provides a mesh-independent contact load measure where the active contact region is a curve rather than an area. Beam-to-beam contact using the radial formulation and edge-to-surface contact contribute to this output variable. Output variable CPOINTLOAD has units of force and helps visualize contact between non-parallel edges where the active contact region can be idealized as a point. The contact stresses, CSTRESS, reflect contributions from surface-to-surface, edge-to-surface, and edge-to-edge contact with units of force per area. 

[Figure 10--1](abc10aqs01.md#rnb-inter-chain-defo-unde) shows initial and deformed configurations of a chain falling under gravity. The individual chain links are meshed with beam, shell, or solid elements such that beam, shell perimeter, and feature edges are activated to participate in edge-to-edge contact. Edge-to-edge contact supplements the edge-to-surface and surface-to-surface contact, which are also active in this model between the individual links and between the chain and the rigid platform. [Figure 10--2](abc10aqs01.md#rnb-inter-chain-cpointload) shows contact load CPOINTLOAD between the edges of the individual links due to edge-to-edge contact. 

**Figure 10–1** Chain falling under gravity onto a rigid platform: initial (left) and deformed (right) configurations.

![](../graphics/rnb-inter-chain-defo-unde.png)

**Figure 10–2** Contour plot of contact load CPOINTLOAD.

![](../graphics/rnb-inter-chain-cpointload.png)

**References: **

**Abaqus Analysis User's Guide**
- ["Abaqus/Standard output variable identifiers," Section 4.2.1](../usb/usb-link.md#usb-out-houtputvar)
- ["Contact interaction analysis: overview," Section 36.1.1](../usb/usb-link.md#usb-cni-acontactoverview)
- ["Defining general contact interactions in Abaqus/Standard," Section 36.2.1](../usb/usb-link.md#usb-cni-acontactgeneralstd)
- ["Surface properties for general contact in Abaqus/Standard," Section 36.2.2](../usb/usb-link.md#usb-cni-asurfacepropassignstd)

**Abaqus Keywords Reference Guide**
- [*CONTACT FORMULATION](../key/key-link.md#usb-kws-hcontformulation)
- [*CONTACT OUTPUT](../key/key-link.md#usb-kws-hcontactoutput)
- [*SURFACE PROPERTY ASSIGNMENT](../key/key-link.md#usb-kws-hsurfpropassign)




