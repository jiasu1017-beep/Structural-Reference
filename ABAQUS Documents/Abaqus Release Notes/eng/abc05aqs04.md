# 5.4 Enhancement to adaptive mesh refinement







**Product: **Abaqus/Explicit  

**Benefits: **You can now apply the adaptive mesh refinement feature to a subset of elements in an Eulerian section.

**Description: **This feature benefits models in which the refinement region remains a small part of an Eulerian domain and does not vary much during the analysis. When the job is run with multiple domains, the elements in this subset can be decomposed independently and assigned to different processors. Load balance between processors can be greatly improved with this approach. For models in which the refinement region varies during the analysis, load imbalance can be reduced through the dynamic load balancing scheme.
**References: **

**Abaqus Analysis User's Guide**
- ["Parallel execution in Abaqus/Explicit," Section 3.5.3](../usb/usb-link.md#usb-int-aparallelexecution)
- ["Defining adaptive mesh refinement in the Eulerian domain," Section 14.1.4](../usb/usb-link.md#usb-anl-aeulerianadaptivemeshrefinement)

**Abaqus Keywords Reference Guide**
- [*ADAPTIVE MESH REFINEMENT](../key/key-link.md#usb-kws-hadaptivemeshrefinement)
- [*DOMAIN DECOMPOSITION](../key/key-link.md#usb-kws-mdomaindecomp)




