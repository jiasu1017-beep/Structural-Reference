# 8.3 Acoustic base motion for SIM-based procedures







**Product: **Abaqus/Standard  

**Benefits: **You can now use acoustic media with prescribed pressure values, with different values for different constraint points in the mode-based analysis (similar to the functionality available in a direct-solution steady-state dynamic analysis). This feature is useful in the automotive industry; for example, to analyze mufflers and fuel tanks.

**Description: **Acoustic pressure base motion is implemented in modal SIM-based transient dynamic and steady-state dynamic (including subspace projection) analyses as “secondary” bases. 

To enable nonzero boundary conditions in the modal analysis, Abaqus uses the “big mass” method. Mathematically, this method is a variant of the penalty method. Abaqus uses secondary base motion to support the nonzero boundary conditions in modal procedures. Named secondary bases are defined by specifying boundary conditions in the frequency extraction step. In consecutive modal analysis steps, these boundary conditions can be associated with amplitude curves and applied as base motions. You can now apply the secondary base motion to the acoustic pressure degree of freedom 8; in previous releases, you could apply the secondary base motion only to the mechanical degrees of freedom (1–6). Because acoustic excitation is a scalar value (as opposed to mechanical degrees of freedom), the orientation of the node is irrelevant.

Acoustic pressure base motions are implemented for the following models:
- acoustic media only
- combined acoustic and structural media; uncoupled modes
- combined acoustic and structural media; coupled modes (modal steady-state dynamic, including subspace projection, analyses only)

**References: **

**Abaqus Analysis User's Guide**
- ["Dynamic analysis procedures: overview," Section 6.3.1](../usb/usb-link.md#usb-anl-adynamicproc)
- ["Prescribed motions in modal superposition procedures" in "Transient modal dynamic analysis," Section 6.3.7](../usb/usb-link.md#usb-anl-amodaldynamic-motion)

**Abaqus Keywords Reference Guide**
- [*BASE MOTION](../key/key-link.md#usb-kws-hbasemotion)




