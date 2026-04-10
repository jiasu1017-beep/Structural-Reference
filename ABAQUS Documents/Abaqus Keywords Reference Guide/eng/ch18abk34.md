# *STEADY STATE DYNAMICS







### *STEADY STATE DYNAMICSSteady-state dynamic response based on harmonic excitation.

This option is used to calculate the system's linearized steady-state response to harmonic excitation.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Direct-solution steady-state dynamic analysis," Section 6.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdyndirect)
- ["Mode-based steady-state dynamic analysis," Section 6.3.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdyn)
- ["Subspace-based steady-state dynamic analysis," Section 6.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdynsubspace)

### **Optional and mutually exclusive parameters (used only if the dynamic response is not based on modal superposition): **

DIRECT

Include this parameter to compute the steady-state harmonic response directly in terms of the physical degrees of freedom of the model. This usually makes the procedure significantly more expensive, but it can be used if model parameters depend on frequency, if the stiffness of the system is unsymmetric and the unsymmetric terms are important, or if the system contains discrete damping (such as dashpot elements).

SUBSPACE PROJECTION

Include this parameter to compute the steady-state harmonic response on the basis of the subspace projection method. In this case a direct solution is obtained for the model projected onto the eigenvectors obtained in the preceding [*FREQUENCY](ch06abk35.md) step. This is a cost-effective approach to including consideration of unsymmetric stiffness and frequency-dependent model parameters. It is more expensive than the modal superposition method but less expensive than the direct-solution method.

Set SUBSPACE PROJECTION=ALL FREQUENCIES (default) if the projection of the dynamic equations onto the modal subspace is to be performed at each frequency requested on the data lines.

Set SUBSPACE PROJECTION=CONSTANT if a single projection of the dynamic equations onto the modal subspace is to be used for all frequencies requested on the data lines. The projection is performed using model properties evaluated at the center frequency determined on a logarithmic or linear scale depending on the value of the FREQUENCY SCALE parameter.

Set SUBSPACE PROJECTION=EIGENFREQUENCY if the projections onto the modal subspace of the dynamic equations are to be performed at each eigenfrequency within the requested ranges and at the eigenfrequencies immediately outside these ranges. The projections are then interpolated at each frequency requested on the data lines. The interpolation is done on a logarithmic or linear scale depending on the value of the FREQUENCY SCALE parameter.

Set SUBSPACE PROJECTION=PROPERTY CHANGE to select how often subspace projections onto the modal subspace are performed based on material property changes as a function of frequency. The interpolation is done on a logarithmic or linear scale depending on the value of the FREQUENCY SCALE parameter.

Set SUBSPACE PROJECTION=RANGE if the projections onto the modal subspace of the dynamic equations are to be performed at the lower limit of each frequency range and at the upper limit of the last frequency range. The interpolation is done on a linear scale. This value can be used only with the SIM architecture.

### **Optional parameters: **

DAMPING CHANGE

This parameter is relevant only for SUBSPACE PROJECTION=PROPERTY CHANGE.

Set this parameter equal to the maximum relative change in damping material properties before a new projection is to be performed. The default value is 0.1.

FREQUENCY SCALE

This parameter is relevant only if INTERVAL=EIGENFREQUENCY or INTERVAL=RANGE. If INTERVAL=SPREAD linear scale is used.

Set this parameter equal to LOGARITHMIC (default) or LINEAR to determine whether a logarithmic or linear scale is used for output. If the SUBSPACE PROJECTION parameter is included and is set equal to either EIGENFREQUENCY or PROPERTY CHANGE, the same scale will be used for the interpolation of the subspace projections.

FRICTION DAMPING

This parameter is relevant only if the DIRECT or the SUBSPACE PROJECTION parameter is included.

Set FRICTION DAMPING=NO (default) or YES to ignore or to include friction-induced damping effects at the slipping contact interface for which a velocity differential is imposed.

INTERVAL

Set INTERVAL=EIGENFREQUENCY if the frequency ranges specified on each data line are to be subdivided using the system's eigenfrequencies. This option requires a preceding [*FREQUENCY](ch06abk35.md) step and is the default if the DIRECT parameter is omitted.

Set INTERVAL=RANGE if the frequency range specified on each data line is to be used directly. This option is the default if the DIRECT parameter is included.

Set INTERVAL=SPREAD to define frequency points around eigenfrequencies found in the frequency ranges specified on each data line. This option requires a preceding [*FREQUENCY](ch06abk35.md) step.

REAL ONLY

This parameter is relevant only if the DIRECT or the SUBSPACE PROJECTION parameter is included.

 Include this parameter if damping terms are to be ignored so that a real, rather than a complex, system matrix is factored. This option can reduce computational time significantly for the DIRECT procedure and, to a lesser extent, for the SUBSPACE PROJECTION procedure.

STIFFNESS CHANGE

This parameter is relevant only for SUBSPACE PROJECTION=PROPERTY CHANGE.

Set this parameter equal to the maximum relative change in stiffness material properties before a new projection is to be performed. The default value is 0.1.

### **Data lines for a steady-state dynamics analysis if INTERVAL=EIGENFREQUENCY: **

**First line:**

Repeat this data line as often as necessary to define frequency ranges in which results are required.

### **Data lines for a steady-state dynamics analysis if INTERVAL=RANGE: **

**First line:**

Repeat this data line as often as necessary to define frequency ranges in which results are required.

### **Data lines for a steady-state dynamics analysis if INTERVAL=SPREAD: **

**First line:**

Repeat this data line as often as necessary to define frequency ranges in which results are required.




