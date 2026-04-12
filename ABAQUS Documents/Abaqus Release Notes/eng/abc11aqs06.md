# 11.6 Enhancements for translating Abaqus data to modal neutral files







**Product: **Abaqus/Standard  

**Benefits: **The translation of Abaqus results to a modal neutral file is significantly faster and the size of the modal neutral file can be significantly smaller than in previous releases.

**Description: **Two enhancements to the **abaqus adams** translator are available. The translator now reads inertia invariants computed during substructure generation rather than computing them, which makes translating the results in an Abaqus substructure SIM database file to an MSC.ADAMS modal neutral (`.mnf`) file significantly faster. Now, the translator only needs to process an “interesting” subset of the displacement modes, which can result in a significantly smaller modal neutral file.
**Reference: **

**Abaqus Analysis User's Guide**
- ["Translating Abaqus data to MSC.ADAMS modal neutral files," Section 3.2.36](../usb/usb-link.md#usb-int-dabaadmproc)




