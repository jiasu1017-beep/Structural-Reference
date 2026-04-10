# *INCIDENT WAVE INTERACTION PROPERTY







### *INCIDENT WAVE INTERACTION PROPERTYDefine the geometric data and fluid properties describing an incident wave.

This option defines the geometric data and fluid properties used to define incident waves. Each [*INCIDENT WAVE INTERACTION](ch09abk10.md) option must refer to an [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md) definition.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Acoustic and shock loads," Section 34.4.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pacoustic)
- [*INCIDENT WAVE INTERACTION](ch09abk10.md)
- [*UNDEX CHARGE PROPERTY](ch20abk02.md)
- [*CONWEP CHARGE PROPERTY](ch03abk76.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the incident wave interaction property in the [*INCIDENT WAVE INTERACTION](ch09abk10.md) option.

### **Optional parameter: **

TYPE

Set TYPE=PLANE (default) to specify a planar incident wave.

Set TYPE=SPHERE to specify a spherical incident wave.

Set TYPE=DIFFUSE to specify a field of planar waves incident from multiple angles.

Set TYPE=AIR BLAST to specify a spherical blast wave. This option is applicable only in an Abaqus/Explicit analysis. 

Set TYPE=SURFACE BLAST to specify a hemispherical blast wave. This option is applicable only in an Abaqus/Explicit analysis. 

### **Data line to define an incident wave interaction property with TYPE=PLANE, TYPE=SPHERE (acoustic decay), or TYPE=SPHERE used in conjunction with the [*UNDEX CHARGE PROPERTY](ch20abk02.md) option: **

**First (and only) line:**

### **Data line to define an incident wave interaction property with TYPE=SPHERE and generalized spatial decay: **

**First (and only) line:**

### **Data line to define incident wave loading from diffuse sources (TYPE=DIFFUSE): **

**First (and only) line:**

### **No data lines are required for TYPE=AIR BLAST or TYPE=SURFACE BLAST used in conjunction with the [*CONWEP CHARGE PROPERTY](ch03abk76.md) option. **




