# 5.6 Parallel enhancement for DEM analysis







**Product: **Abaqus/Explicit  

**Benefits: **Discrete element method (DEM) simulations run more efficiently due to domain decomposition of the DEM computations.

**Description: **Computations associated with DEM particle contact are now implemented in domain parallel, enabling better parallel scaling if multiple CPUs are used. Similar to parallel smoothed particle hydrodynamic (SPH) analysis, an evolving domain decomposition is used to avoid large spatial overlap among DEM domains (and, therefore, to maintain good parallel scaling) after large relative motions of DEM particles.
**Reference: **

**Abaqus Analysis User's Guide**
- ["Discrete element method," Section 15.1.1](../usb/usb-link.md#usb-anl-ademanalysis)




