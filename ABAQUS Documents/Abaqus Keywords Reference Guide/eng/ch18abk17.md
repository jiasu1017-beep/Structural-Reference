# *SIMPEDANCE







### *SIMPEDANCEDefine impedances of acoustic surfaces.

This option is used to provide surface impedance information or nonreflecting boundaries for acoustic and coupled acoustic-structural analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Acoustic, shock, and coupled acoustic-structural analysis," Section 6.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aacoustic)
- ["Acoustic and shock loads," Section 34.4.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pacoustic)
- [*IMPEDANCE](ch09abk01.md)
- [*IMPEDANCE PROPERTY](ch09abk02.md)

### **Required, mutually exclusive parameters: **

PROPERTY

Set this parameter equal to the name of the [*IMPEDANCE PROPERTY](ch09abk02.md) option defining the table of impedance values to be used.

NONREFLECTING

Set NONREFLECTING=PLANAR (default) to specify the impedance corresponding to that of a normal incidence plane wave.

Set NONREFLECTING=IMPROVED to specify the impedance corresponding to that of a plane wave at an arbitrary angle of incidence. This parameter can be used only for transient dynamics.

Set NONREFLECTING=CIRCULAR to specify a radiation condition appropriate for a circular boundary in two dimensions or a right circular cylinder in three dimensions.

Set NONREFLECTING=SPHERICAL to specify a radiation condition appropriate for a spherical boundary.

Set NONREFLECTING=ELLIPTICAL to specify a radiation condition appropriate for an elliptical boundary in two dimensions or a right elliptical cylinder in three dimensions.

Set NONREFLECTING=PROLATE SPHEROIDAL to specify a radiation condition appropriate for a prolate spheroidal boundary.

### **Optional parameter: **

OP

Set OP=MOD (default) to modify existing impedances or to define additional impedances. 

Set OP=NEW if all existing impedances applied to the model should be removed. To remove only selected impedances, use OP=NEW and respecify all impedances that are to be retained.

### **Data line to define an impedance for PROPERTY, NONREFLECTING=PLANAR, or NONREFLECTING=IMPROVED: **

**First (and only) line:**

### **Data line to define an absorbing boundary impedance for NONREFLECTING=CIRCULAR or NONREFLECTING=SPHERICAL: **

**First (and only) line:**

### **Data line to define an absorbing boundary impedance for NONREFLECTING=ELLIPTICAL or NONREFLECTING=PROLATE SPHEROIDAL: **

**First (and only) line:**




