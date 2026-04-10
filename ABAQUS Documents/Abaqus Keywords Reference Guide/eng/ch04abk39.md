# *DSECURRENT







### *DSECURRENTSpecify distributed current densities over a surface in an electromagnetic analysis.

This option is used to input distributed current densities over a surface in coupled thermal-electrical, coupled thermal-electrical-structural, eddy current, and magnetostatic analyses.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Coupled thermal-electrical analysis," Section 6.7.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ajouleheating)
- ["Fully coupled thermal-electrical-structural analysis," Section 6.7.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acoupthermalelecstruct)
- ["Eddy current analysis," Section 6.7.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeddycurrent)
- ["Magnetostatic analysis," Section 6.7.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amagnetostatic)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the electric current density during the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)).

OP

Set OP=MOD (default) for existing [*DSECURRENT](ch04abk39.md)s to remain, with this option defining distributed current densities to be added or modified.

Set OP=NEW if all existing [*DSECURRENT](ch04abk39.md)s applied to the model should be removed.

### **Optional, mutually exclusive parameters for time-harmonic eddy current analyses: **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the surface current density.

REAL

Include this parameter (default) to define the real (in-phase) part of the surface current density.

### **Data lines to define distributed electrical current densities in coupled thermal-electrical or coupled thermal-electrical-structural analyses: **

**First line:**

Repeat this data line as often as necessary to define current densities for various surfaces.

### **Data lines to define surface current densities in eddy current or magnetostatic analyses: **

**First line:**

Repeat this data line as often as necessary to define surface current densities for various surfaces.




