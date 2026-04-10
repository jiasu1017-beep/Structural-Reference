# *COMPLEX FREQUENCY







### *COMPLEX FREQUENCYExtract complex eigenvalues and modal vectors.

This option is used to perform eigenvalue extraction to calculate the complex eigenvalues and corresponding complex mode shapes of a system.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Complex eigenvalue extraction," Section 6.3.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acomplexfreqextract)

### **Optional parameters: **

FRICTION DAMPING

Set FRICTION DAMPING=NO (default) to ignore friction-induced damping effects.

Set FRICTION DAMPING=YES to include friction-induced damping effects.

NORMALIZATION

Set NORMALIZATION=DISPLACEMENT (default for SIM-based analyses) to normalize the complex eigenvectors so that the real part of the largest value in each vector is unity and the imaginary part is zero.

Set NORMALIZATION=MODAL (the only option for analyses that are not based on the SIM architecture) to normalize only the complex eigenvectors of the projected system.

PROPERTY EVALUATION

Set this parameter equal to the frequency at which to evaluate frequency-dependent properties for viscoelasticity, springs, and dashpots during complex eigenvalue extraction. If this parameter is omitted, Abaqus/Standard will evaluate the material properties associated with frequency-dependent springs and dashpots at zero frequency and will not consider the contributions from frequency-domain viscoelasticity in the [*COMPLEX FREQUENCY](ch03abk26.md) step.

UNSTABLE MODES ONLY

Set this parameter equal to the cutoff value for complex modes. Only complex modes with the real part of the eigenvalue higher than the cutoff value are written to the output database (`.odb`) file. The default value of this parameter is 0.0. If this parameter is omitted, all complex modes are output.

### **Optional, mutually exclusive parameters: **

LEFT EIGENVECTORS

Include this parameter to request left complex eigenvectors. This parameter is relevant only in analyses that are based on the SIM architecture.

RIGHT EIGENVECTORS

Include this parameter (default) to request right complex eigenvectors.

### **Data line for complex eigenvalue extraction: **

**First (and only) line:**




