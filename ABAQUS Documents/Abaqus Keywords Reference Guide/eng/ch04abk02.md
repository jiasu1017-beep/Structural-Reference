# *D EM POTENTIAL







### *D EM POTENTIALSpecify distributed surface magnetic vector potential.

This option is used to prescribe distributed surface magnetic vector potential in an eddy current or in a magnetostatic analysis.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Eddy current analysis," Section 6.7.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeddycurrent)
- ["Magnetostatic analysis," Section 6.7.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amagnetostatic)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the variation of the magnetic vector potential magnitude during the step with respect to frequency for time-harmonic eddy current analysis or with respect to time for transient eddy current and magnetostatic analyses.

Amplitude references are ignored for nonuniform potentials given by user subroutine [`UDEMPOTENTIAL`](../sub/sub-link.md#sub-xsl-udempotential).

Only the magnitude of the magnetic vector potential is changed with frequency or time. The direction (or both the real and imaginary parts of the direction for a time-harmonic eddy current analysis) of the magnetic vector potential is not changed.

OP

Set OP=MOD (default) for existing [*D EM POTENTIAL](ch04abk02.md)s to remain, with this option modifying existing distributed magnetic vector potentials or defining additional distributed magnetic vector potentials.

Set OP=NEW if all existing [*D EM POTENTIAL](ch04abk02.md)s applied to the model should be removed. New distributed magnetic vector potentials can be defined.

### **Data lines to define distributed surface magnetic vector potentials in a time-harmonic eddy current analysis: **

**First line:**

Repeat this data line as often as necessary to define distributed magnetic vector potentials on different surfaces.

### **Data lines to define distributed surface magnetic vector potentials in a transient eddy current analysis or in a magnetostatic analysis: **

**First line:**

Repeat this data line as often as necessary to define distributed magnetic vector potentials on different surfaces.




