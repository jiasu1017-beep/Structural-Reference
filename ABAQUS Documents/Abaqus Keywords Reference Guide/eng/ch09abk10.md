# *INCIDENT WAVE INTERACTION







### *INCIDENT WAVE INTERACTIONDefine incident wave loading for a blast or scattering load on a surface.

This option is used to apply incident wave loading. The [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md) option must be used in conjunction with the [*INCIDENT WAVE INTERACTION](ch09abk10.md) option. If the incident wave field includes a reflection off a plane outside the boundaries of the mesh, this effect can be modeled with the [*INCIDENT WAVE REFLECTION](ch09abk13.md) option. The incident wave interaction can be used in steady-state dynamic procedures to define individual wave sources or loading from diffuse sources.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Acoustic, shock, and coupled acoustic-structural analysis," Section 6.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aacoustic)
- ["Acoustic and shock loads," Section 34.4.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pacoustic)
- [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md)
- [*INCIDENT WAVE REFLECTION](ch09abk13.md)

### **Required parameter: **

PROPERTY

Set this parameter equal to the name of the [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md) option defining the incident wave field.

### **Required, mutually exclusive parameters: **

ACCELERATION AMPLITUDE

Set this parameter equal to the name of the amplitude curve defining the fluid particle acceleration time history at the standoff point (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). This amplitude curve will be used to compute the fluid traction *only*: a solid surface requiring a pressure load cannot be specified on the data line of an [*INCIDENT WAVE INTERACTION](ch09abk10.md) option if the ACCELERATION AMPLITUDE parameter is used.

This parameter is valid only for transient planar incident waves using the [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md), TYPE=PLANE option. Reflected loads, using the [*INCIDENT WAVE REFLECTION](ch09abk13.md) option, are not permitted in this case.

CONWEP

This parameter applies only to Abaqus/Explicit analyses.

Include this parameter to define an incident wave using the [*CONWEP CHARGE PROPERTY](ch03abk76.md) option. This parameter is valid only for blast waves using the [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md), TYPE=AIR BLAST or TYPE=SURFACE BLAST option.

PRESSURE AMPLITUDE

Set this parameter equal to the name of the amplitude curve defining the fluid pressure time history at the standoff point (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). The corresponding fluid traction, if required, will be computed from the pressure amplitude reference.

UNDEX

Include this parameter to define a spherical incident wave using the [*UNDEX CHARGE PROPERTY](ch20abk02.md) option. This parameter is valid only for spherical incident waves using the [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md), TYPE=SPHERE option.

### **Optional, mutually exclusive parameters for matrix generation and steady-state dynamics analysis (direct or subspace): **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the loading at the standoff point.

REAL

Include this parameter (default) to define the real (in-phase) part of the loading at the standoff point.

### **Data line to define an incident wave when the CONWEP parameter is omitted: **

**First (and only) line:**

### **Data line to define an incident wave when the CONWEP parameter is included: **

**First (and only) line:**




