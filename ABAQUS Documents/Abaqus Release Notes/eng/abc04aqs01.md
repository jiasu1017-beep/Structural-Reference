# 4.1 The AMS eigensolver can extract coupled structural-acoustic eigenmodes







**Product: **Abaqus/Standard  

**Benefits: **The coupled structural-acoustic eigenmodes can be computed by the AMS eigensolver and stored using the  SIM architecture. In addition, the modal methods can utilize these modes for modal superposition.

**Description: **If the model includes structural-acoustic coupling, the AMS eigensolver can extract coupled modes. Previously, this functionality was available only with the Lanczos eigensolver. This enhancement allows you to take advantage of the superior performance offered by the AMS eigensolver. For example, extracting about 1,000 coupled modes of a 2.5 million degree-of-freedom car body model takes 3 hours and 3 minutes with the Lanczos eigensolver; the AMS eigensolver needs only 32 minutes, which is almost six times faster. This benchmarking was performed using 16 cores on a Sandy Bridge machine with 128 GB of memory.

The coupled structural-acoustic modes computed by the AMS eigensolver are supported in the following modal procedures that use the SIM architecture:
- complex eigenvalue extraction,
- mode-based steady-state dynamic analysis,
- subspace-based steady-state dynamic analysis, and
- substructure generation.

**References: **

**Abaqus Analysis User's Guide**
- ["Natural frequency extraction," Section 6.3.5](../usb/usb-link.md#usb-anl-afreqextraction)

**Abaqus Keywords Reference Guide**
- [*COMPLEX FREQUENCY](../key/key-link.md#usb-kws-hcomplexfrequency)
- [*FREQUENCY](../key/key-link.md#usb-kws-hfrequency)
- [*STEADY STATE DYNAMICS](../key/key-link.md#usb-kws-hsteadystdyn)
- [*SUBSTRUCTURE GENERATE](../key/key-link.md#usb-kws-ssubgenerate)

**Abaqus Theory Guide**
- ["Coupled acoustic-structural medium analysis," Section 2.9.1](../stm/stm-link.md#stm-anl-acouststruct)




