# 10.2 Improved contact at complex intersections in Abaqus/Explicit







**Product: **Abaqus/Explicit  

**Benefits: **Contact at complex intersections (edges connected to more than two faces) is improved.

**Description: **    Surface offsets at complex intersections were always set to zero in previous releases of Abaqus/Explicit, even if you specified a nonzero reference surface offset for the underlying elements. This limitation sometimes caused undesirable solution behavior. It is removed in the current release.

[Figure 10--3](abc10aqs02.md#rnb614-complex-int) shows a scenario in which a block slides along shell elements whose reference surface corresponds to the bottom surface of a shell. The bottom surface of the shell happens to correspond to the shell reference surface because a nonzero offset has been specified. The fact that the larger body has a T-junction should not be particularly relevant to this model, but the previous limitation (surface offset set to zero) caused the T-junction to have a large effect. 

Shell element thickness profiles are represented in [Figure 10--3](abc10aqs02.md#rnb614-complex-int), but these profiles do not reflect the effect of the previous limitation on the contact surface geometry. The sequence of four deformed-configuration plots at the top of [Figure 10--3](abc10aqs02.md#rnb614-complex-int) shows the effect of the previous limitation as the block nears the T-junction: a gap appears between the bodies (even though significant contact forces are still being transmitted). Solution noise remains in this example even after the block is well past the T-junction. The sequence of plots at the bottom of [Figure 10--3](abc10aqs02.md#rnb614-complex-int) shows the improved (physically realistic) behavior. In this case the block simply slides along the other body as expected, with very little deformation of either part.

This enhancement is in effect by default.

**Figure 10–3** Block sliding on a flat portion of a T-junction structure with the previous behavior (top) and current behavior (bottom).

![](../graphics/rnb614-complex-int.png)

**Reference: **

**Abaqus Analysis User's Guide**
- ["Surface offset" in "Assigning surface properties for general contact in Abaqus/Explicit," Section 36.4.2](../usb/usb-link.md#usb-cni-asurfacepropassign-offset)




